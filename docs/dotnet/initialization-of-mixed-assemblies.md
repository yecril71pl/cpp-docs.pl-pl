---
title: Inicjalizacja zestawów mieszanych
ms.date: 03/09/2018
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 35dd47bd87c278d60fc616dca854bf843acc7c57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501232"
---
# <a name="initialization-of-mixed-assemblies"></a>Inicjalizacja zestawów mieszanych

Deweloperzy systemu Windows muszą zawsze być ostrożność blokady modułu ładującego podczas `DllMain`uruchamiania kodu. Istnieje jednak kilka dodatkowych problemów, które należy wziąć pod uwagę podczas C++pracy z zestawami trybów w trybie mieszanym.

Kod w [DllMain](/windows/win32/Dlls/dllmain) nie może uzyskać dostępu do środowiska uruchomieniowego języka wspólnego (CLR) platformy .NET. Oznacza to, `DllMain` że nie należy wykonywać wywołań do funkcji zarządzanych, bezpośrednio ani pośrednio; żaden kod zarządzany nie powinien być zadeklarowany `DllMain`ani zaimplementowany w programie; i nie powinno `DllMain` być wykonywane odzyskiwanie pamięci ani automatyczne ładowanie biblioteki. .

## <a name="causes-of-loader-lock"></a>Przyczyny blokady modułu ładującego

Po wprowadzeniu platformy .NET istnieją dwa różne mechanizmy ładowania modułu wykonawczego (EXE lub DLL): jeden dla systemu Windows, który jest używany dla modułów niezarządzanych, a drugi dla środowiska CLR, który ładuje zestawy .NET. Mieszana Biblioteka DLL ładująca centra problemów wokół modułu ładującego systemu operacyjnego Microsoft Windows.

Gdy zestaw zawierający tylko konstrukcje .NET jest ładowany do procesu, moduł ładujący CLR może wykonać wszystkie niezbędne zadania ładowania i inicjalizacji. Jednak w przypadku zestawów mieszanych, ponieważ mogą one zawierać kod natywny i dane, należy również użyć modułu ładującego systemu Windows.

Moduł ładujący systemu Windows gwarantuje, że żaden kod nie może uzyskać dostępu do kodu lub danych w tej bibliotece DLL, zanim zostanie zainicjowany, i że żaden kod nie może nadmiarowo załadować biblioteki DLL, gdy zostanie ona częściowo zainicjowana. W tym celu moduł ładujący systemu Windows korzysta z sekcji krytycznej dla procesu (często nazywanej "blokadą modułu ładującego"), która uniemożliwia niebezpieczny dostęp podczas inicjowania modułu. W efekcie proces ładowania jest narażony na wiele klasycznych scenariuszy zakleszczenia. W przypadku zestawów mieszanych następujące dwa scenariusze zwiększają ryzyko zakleszczenia:

- Po pierwsze, jeśli użytkownicy próbują wykonać funkcje skompilowane do języka pośredniego firmy Microsoft (MSIL), gdy blokada `DllMain` modułu ładującego jest utrzymywana (na przykład z lub w statycznych inicjatorach), może to spowodować zakleszczenie. Rozważ przypadek, w którym funkcja MSIL odwołuje się do typu w zestawie, który nie został załadowany. Środowisko CLR podejmie próbę automatycznego załadowania tego zestawu, co może wymagać, aby program ładujący Windows mógł blokować blokadę modułu ładującego. Występuje zakleszczenie, ponieważ blokada modułu ładującego jest już zatrzymywana przez kod wcześniej w sekwencji wywołania. Jednak wykonanie MSIL w ramach blokady modułu ładującego nie gwarantuje, że wystąpi zakleszczenie, co sprawia, że ten scenariusz trudno jest zdiagnozować i naprawić. W pewnych okolicznościach, takich jak, gdy biblioteka DLL typu, którego dotyczy odwołanie, nie zawiera natywnych konstrukcji, a wszystkie jego zależności nie zawierają natywnych konstrukcji, moduł ładujący systemu Windows nie jest wymagany do załadowania zestawu platformy .NET dla przywoływanego typu. Ponadto wymagany zestaw lub jego mieszane zależności natywne/. NET mogły być już załadowane przez inny kod. W związku z tym zakleszczenie może być trudne do przewidywania i może się różnić w zależności od konfiguracji maszyny docelowej.

- Po drugie, podczas ładowania bibliotek DLL w wersjach 1,0 i 1,1 .NET Framework, środowisko CLR zakłada, że blokada modułu ładującego nie została wstrzymana i wykonuje kilka akcji, które są nieprawidłowe w ramach blokady modułu ładującego. Przy założeniu, że blokada modułu ładującego nie jest założeń dla czystych bibliotek dll platformy .NET, ale ponieważ mieszane biblioteki DLL wykonują natywne procedury inicjowania, wymagają natywnego modułu ładującego Windows, a w związku z tym blokadę modułu ładującego. W związku z tym nawet jeśli deweloper nie próbował wykonać żadnych funkcji MSIL podczas inicjacji biblioteki DLL, nadal istniała niewielka możliwość zakleszczenia niedeterministyczna z wersjami 1,0 i 1,1 .NET Framework.

Wszystkie inne niż determiny zostały usunięte z procesu ładowania mieszanej biblioteki DLL. Zostało wykonane z następującymi zmianami:

- Środowisko CLR nie tworzy już fałszywych założeń podczas ładowania mieszanych bibliotek DLL.

- Inicjalizacja niezarządzana i zarządzana jest wykonywana w dwóch oddzielnych i odrębnych etapach. Niezarządzana Inicjalizacja odbywa się najpierw (za pośrednictwem DllMain), a Inicjalizacja zarządzana odbywa się później za pośrednictwem. Konstrukcja obsługiwana `.cctor` przez sieć. Drugie jest całkowicie niewidoczne dla użytkownika, chyba że są używane **/zl** lub **/NODEFAULTLIB** . Zobacz[/NODEFAULTLIB (Ignoruj biblioteki)](../build/reference/nodefaultlib-ignore-libraries.md) i [/zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) , aby uzyskać więcej informacji.

Blokada modułu ładującego może nadal wystąpić, ale teraz występuje reproducibly i wykryto. Jeśli `DllMain` zawiera instrukcje MSIL, kompilator generuje [Ostrzeżenie kompilatora ostrzeżenia (poziom 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Ponadto CRT lub CLR spróbuje wykryć i zgłosić próbę wykonania MSIL przy użyciu blokady modułu ładującego. W wyniku wykrywania CRT Wystąpił błąd czasu wykonania diagnostyki środowiska uruchomieniowego C R6033.

W pozostałej części niniejszego dokumentu opisano pozostałe scenariusze, dla których można wykonać instrukcje MSIL w ramach blokady modułu ładującego, rozwiązania problemu w ramach każdego z tych scenariuszy i techniki debugowania.

## <a name="scenarios-and-workarounds"></a>Scenariusze i obejścia

Istnieje kilka różnych sytuacji, w których kod użytkownika może wykonywać MSIL pod blokadą modułu ładującego. Deweloper musi upewnić się, że implementacja kodu użytkownika nie próbuje wykonać instrukcji MSIL w każdym z tych sytuacji. W poniższych podsekcjach opisano wszystkie możliwości dyskusji o sposobie rozwiązywania problemów w najczęstszych przypadkach.

### <a name="dllmain"></a>DllMain

`DllMain` Funkcja jest punktem wejścia zdefiniowanym przez użytkownika dla biblioteki DLL. Chyba że użytkownik określi inaczej, `DllMain` jest wywoływana za każdym razem, gdy proces lub wątek dołączy lub odłącza się od zawierającej dll. Ponieważ to wywołanie może wystąpić, gdy blokada modułu ładującego jest utrzymywana, nie należy kompilować `DllMain` funkcji podanej przez użytkownika do MSIL. Ponadto żadna funkcja w drzewie `DllMain` wywołań nie może zostać skompilowana do MSIL. Aby rozwiązać problemy w tym miejscu, blok kodu, `DllMain` który definiuje się, powinien `unmanaged`zostać zmodyfikowany za pomocą #pragma. Należy to zrobić dla każdej funkcji, która `DllMain` wywołuje.

W przypadkach, gdy te funkcje muszą wywoływać funkcję, która wymaga implementacji MSIL dla innych kontekstów wywoływania, można użyć strategii duplikowania, w której tworzone są zarówno środowisko .NET, jak i natywna wersja tej samej funkcji.

Alternatywnie, jeśli `DllMain` nie jest to wymagane lub jeśli nie trzeba go wykonywać w ramach blokady modułu ładującego, można usunąć implementację dostarczoną `DllMain` przez użytkownika, co spowoduje eliminację problemu.

Jeśli DllMain próbuje wykonać polecenie MSIL bezpośrednio, zostanie [wyświetlone ostrzeżenie kompilatora (poziom 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) . Jednak kompilator nie może wykryć przypadków, w których DllMain wywołuje funkcję w innym module, który z kolei próbuje wykonać MSIL.

Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [przeszkody do diagnozowania](#impediments-to-diagnosis).

### <a name="initializing-static-objects"></a>Inicjowanie obiektów statycznych

Inicjowanie obiektów statycznych może spowodować zakleszczenie, jeśli wymagany jest inicjator dynamiczny. W przypadku prostych przypadków, na przykład gdy zmienna statyczna jest przypisana do wartości znanej w czasie kompilacji, nie jest wymagana żadna Inicjalizacja dynamiczna, więc nie istnieje ryzyko zakleszczenia. Jednak zmienne statyczne inicjowane przez wywołania funkcji, wywołania konstruktora lub wyrażenia, które nie mogą być oceniane w czasie kompilacji, wymagają wykonania kodu podczas inicjowania modułu.

Poniższy kod przedstawia przykłady inicjatorów statycznych, które wymagają inicjalizacji dynamicznej: wywołania funkcji, konstruowania obiektu i inicjowania wskaźnika. (Te przykłady nie są statyczne, ale są zakładane zgodnie z definicją w zakresie globalnym, który ma ten sam skutek).

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

To ryzyko zakleszczenia zależy od tego, czy zawierający go moduł jest kompilowany z **/CLR** i czy zostanie wykonane. W odróżnieniu od tego, czy zmienna statyczna jest skompilowana bez **/CLR** (lub znajduje `unmanaged` się w bloku #pragma), a inicjator dynamiczny wymagany do jego zainicjowania powoduje wykonanie instrukcji MSIL, może wystąpić zakleszczenie. Jest to spowodowane tym, że w przypadku modułów skompilowanych bez **/CLR**Inicjalizacja zmiennych statycznych jest wykonywana przez DllMain. Natomiast zmienne statyczne skompilowane z **/CLR** są inicjowane przez `.cctor`program, po zakończeniu etapu inicjalizacji niezarządzanej i wydaniu blokady modułu ładującego.

Istnieje wiele rozwiązań do zakleszczenia spowodowanych dynamiczną inicjalizacją zmiennych statycznych (uporządkowane w sposób niezbędny do rozwiązania problemu):

- Plik źródłowy zawierający zmienną statyczną można skompilować za pomocą **/CLR**.

- Wszystkie funkcje wywoływane przez zmienną statyczną mogą być kompilowane do kodu natywnego za pomocą `unmanaged` dyrektywy #pragma.

- Ręcznie Sklonuj kod, od którego zależy zmienna statyczna, co zapewnia zarówno .NET, jak i natywną wersję o różnych nazwach. Deweloperzy mogą następnie wywoływać natywną wersję z natywnych inicjatorów statycznych i wywoływać platformę .NET w innym miejscu.

### <a name="user-supplied-functions-affecting-startup"></a>Funkcje dostarczane przez użytkownika mające wpływ na uruchamianie

Istnieje kilka funkcji dostarczonych przez użytkownika, w których biblioteki są zależne od inicjalizacji podczas uruchamiania. Na przykład, gdy operatory przeciążania globalnie w C++ taki sposób, `new` jak `delete` operatory i, są używane w dowolnym miejscu, w tym w C++ przypadku inicjalizacji i zniszczenia biblioteki standardowej. W związku z tym C++ , biblioteki standardowe i inicjatory udostępniane przez użytkownika będą wywoływały wszystkie wersje tych operatorów podane przez użytkownika.

Jeśli wersje dostarczone przez użytkownika są kompilowane na potrzeby MSIL, wówczas te inicjatory próbują wykonać instrukcje MSIL podczas przechowywania blokady modułu ładującego. Dostarczony `malloc` przez użytkownika ma takie same konsekwencje. Aby rozwiązać ten problem, dowolne z tych przeciążeń lub definicji dostarczonych przez użytkownika musi zostać zaimplementowane jako kod natywny `unmanaged` za pomocą dyrektywy #pragma.

Aby uzyskać więcej informacji na temat tego scenariusza, zobacz [przeszkody do diagnozowania](#impediments-to-diagnosis).

### <a name="custom-locales"></a>Niestandardowe ustawienia regionalne

Jeśli użytkownik udostępnia niestandardowe globalne ustawienia regionalne, te ustawienia regionalne będą używane do inicjowania wszystkich przyszłych strumieni we/wy, w tym strumieni, które są inicjowane statycznie. Jeśli ten globalny obiekt ustawień regionalnych jest kompilowany do MSIL, to funkcje elementów członkowskich obiektu skompilowane do MSIL mogą być wywoływane, gdy blokada modułu ładującego jest utrzymywana.

Istnieją trzy opcje rozwiązania tego problemu:

Pliki źródłowe zawierające wszystkie definicje strumienia operacji we/wy można skompilować przy użyciu opcji **/CLR** . Uniemożliwia wykonanie statycznych inicjatorów w ramach blokady modułu ładującego.

Definicje funkcji niestandardowych ustawień regionalnych można kompilować do kodu natywnego za pomocą dyrektywy #pragma `unmanaged` .

Należy zrezygnować z ustawiania niestandardowych ustawień regionalnych jako globalnych ustawień regionalnych do momentu zwolnienia blokady modułu ładującego. Następnie jawnie Skonfiguruj strumienie we/wy utworzone podczas inicjowania przy użyciu niestandardowych ustawień regionalnych.

## <a name="impediments-to-diagnosis"></a>Przeszkody do diagnostyki

W niektórych przypadkach trudno jest wykryć Źródło zakleszczeniów. W poniższych podsekcjach omówiono te scenariusze i sposoby obejścia tych problemów.

### <a name="implementation-in-headers"></a>Implementacja w nagłówkach

W wybranych przypadkach implementacje funkcji wewnątrz plików nagłówkowych mogą komplikują diagnostykę. Funkcje wbudowane i kod szablonu wymagają, aby funkcje zostały określone w pliku nagłówkowym.  C++ Język Określa regułę jednej definicji, która wymusza, aby wszystkie implementacje funkcji o tej samej nazwie były semantycznie równoważne. W związku z C++ tym konsolidator nie musi wprowadzać żadnych specjalnych zagadnień podczas scalania plików obiektów, które mają zduplikowane implementacje danej funkcji.

Przed rozpoczęciem korzystania z programu Visual Studio 2005, konsolidator po prostu wybiera największą z tych semantycznie równoważnych definicji, aby uwzględnić deklaracje przesyłania dalej, oraz scenariusze, w których różne opcje optymalizacji są używane dla różnych plików źródłowych. Tworzy problem dla mieszanych bibliotek DLL/. NET.

Ponieważ ten sam nagłówek może być dołączany C++ do plików z włączonym **/CLR** i wyłączonym lub #include może być `#pragma unmanaged` opakowany wewnątrz bloku, możliwe jest posiadanie zarówno języka MSIL, jak i natywnej wersji funkcji, które udostępniają implementacje w nagłówka. Implementacje MSIL i natywne mają różną semantykę w odniesieniu do inicjalizacji w ramach blokady modułu ładującego, która efektywnie narusza jedną regułę definicji. W związku z tym, gdy konsolidator wybiera największą implementację, może wybrać wersję MSIL funkcji, nawet jeśli została ona jawnie skompilowana do kodu natywnego w innym miejscu przy użyciu niezarządzanej dyrektywy #pragma. Aby upewnić się, że wersja MSIL szablonu lub funkcja wbudowana nigdy nie jest wywoływana w ramach blokady modułu ładującego, każda definicja każdej takiej funkcji wywołana w bloku Loader musi `#pragma unmanaged` zostać zmodyfikowana z dyrektywą. Jeśli plik nagłówka pochodzi od innej firmy, najprostszym sposobem wprowadzenia tej zmiany jest wypchnięcie i wyskakujące `#pragma unmanaged` dyrektywy dotyczącej dyrektywy #include dla pliku nagłówkowego, którego dotyczy problem. (Zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) na przykład). Jednak ta strategia nie będzie działała w przypadku nagłówków zawierających inny kod, który musi bezpośrednio wywołać interfejsy API platformy .NET.

Jako wygoda dla użytkowników zajmujących się blokadą modułu ładującego, konsolidator wybierze implementację natywną dla zarządzanego elementu, gdy jest prezentowany. Ta wartość domyślna pozwala uniknąć powyższych problemów. Istnieją jednak dwa wyjątki od tej reguły w tej wersji z powodu dwóch nierozwiązanych problemów z kompilatorem:

- Wywołanie funkcji wbudowanej odbywa się za pomocą globalnego wskaźnika funkcji statycznej. Ten scenariusz jest istotny, ponieważ funkcje wirtualne są wywoływane za poorednictwem globalnych wskaźników funkcji. Na przykład

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>Diagnozowanie w trybie debugowania

Wszystkie diagnozy problemów z blokadą modułu ładującego należy przeprowadzić z kompilacjami debugowania. Kompilacje wydań mogą nie generować diagnostyki, a optymalizacje wykonywane w trybie zwolnienia mogą maskować niektóre MSIL w obszarze scenariusze blokowania modułu ładującego.

## <a name="how-to-debug-loader-lock-issues"></a>Jak debugować problemy z blokadą modułu ładującego

Diagnostyka generowana przez środowisko CLR, gdy wywoływana jest funkcja MSIL powoduje zawieszenie wykonywania przez środowisko CLR. Z kolei, które powoduje, że C++ debuger trybu mieszanego w trybie mieszanym jest również używany podczas procesu debugowanego obiektu. Jednak podczas dołączania do procesu nie jest możliwe uzyskanie zarządzanego stosu wywołań dla debugowanego obiektu przy użyciu debugera mieszanego.

Aby zidentyfikować konkretną funkcję MSIL, która została wywołana w ramach blokady modułu ładującego, deweloperzy powinni wykonać następujące czynności:

1. Upewnij się, że symbole biblioteki Mscoree. dll i mscorwks. dll są dostępne.

   Symbole można udostępnić na dwa sposoby. Najpierw można dodać plików PDB dla bibliotek mscoree. dll i mscorwks. dll do ścieżki wyszukiwania symboli. Aby je dodać, Otwórz okno dialogowe Opcje ścieżki wyszukiwania symboli. (Z menu **Narzędzia** wybierz polecenie **Opcje**. W lewym okienku okna dialogowego **Opcje** Otwórz węzeł **debugowanie** i wybierz pozycję **symbole**. Dodaj ścieżkę do plików. mscoree. dll i mscorwks. dll do listy wyszukiwania. Te plików PDB są zainstalowane w%VSINSTALLDIR%\SDK\v2.0\symbols. Wybierz **OK**.

   Następnie można pobrać plików PDB dla biblioteki Mscoree. dll i mscorwks. dll z serwera symboli firmy Microsoft. Aby skonfigurować serwer symboli, Otwórz okno dialogowe Opcje ścieżki wyszukiwania symboli. (Z menu **Narzędzia** wybierz polecenie **Opcje**. W lewym okienku okna dialogowego **Opcje** Otwórz węzeł **debugowanie** i wybierz pozycję **symbole**. Dodaj tę ścieżkę wyszukiwania do listy wyszukiwania: `https://msdl.microsoft.com/download/symbols`. Dodaj Katalog pamięci podręcznej symboli do pola tekstowego pamięć podręczna serwera symboli. Wybierz **OK**.

1. Ustaw tryb debugera na tryb tylko natywny.

   Otwórz siatkę **Właściwości** dla projektu startowego w rozwiązaniu. Wybierz pozycję**debugowanie** **Właściwości** > konfiguracji. Ustaw **Typ debugera** na **tylko natywny**.

1. Uruchom Debuger (F5).

1. Po wygenerowaniu diagnostyki **/CLR** wybierz pozycję **Ponów próbę** , a następnie wybierz pozycję **Przerwij**.

1. Otwórz okno stosu wywołań. (Na pasku menu wybierz kolejno opcje **Debuguj** > **stos wywołań** **systemu Windows** > ). Inicjator powodujący `DllMain` problemy lub statyczny jest identyfikowany za pomocą zielonej strzałki. Jeśli nie zostanie zidentyfikowana funkcja powodująca problemy, należy wykonać następujące czynności, aby je znaleźć.

1. Otwórz okno **bezpośrednie** (na pasku menu wybierz polecenie **Debuguj** > **okna** > **natychmiast**.)

1. Wprowadź `.load sos.dll` w oknie **bezpośrednim** , aby załadować usługę debugowania SOS.

1. Przejdź `!dumpstack` do okna **bezpośredniego** , aby uzyskać pełną listę wewnętrznego stosu **/CLR** .

1. Wyszukaj pierwsze wystąpienie (najbliżej dołu stosu) _CorDllMain (Jeśli `DllMain` powoduje problem) lub _VTableBootstrapThunkInitHelperStub lub GetTargetForVTableEntry (Jeśli inicjator statyczny powoduje problem). Wpis stosu tuż poniżej tego wywołania to wywołanie funkcji MSIL zaimplementowane, która podjęła próbę wykonania w ramach blokady modułu ładującego.

1. Przejdź do pliku źródłowego i numeru wiersza zidentyfikowanego w poprzednim kroku, a następnie Rozwiąż problem, korzystając z scenariuszy i rozwiązań opisanych w sekcji scenariusze.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje, jak uniknąć blokady modułu ładującego, przenosząc kod z `DllMain` do konstruktora obiektu globalnego.

W tym przykładzie istnieje globalny obiekt zarządzany, którego Konstruktor zawiera zarządzany obiekt, który został pierwotnie `DllMain`utworzony. Druga część tego przykładu odwołuje się do zestawu, tworząc wystąpienie obiektu zarządzanego w celu wywołania konstruktora modułu, który wykonuje inicjalizację.

### <a name="code"></a>Kod

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker does not throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

Ten przykład ilustruje problemy związane z inicjalizacją zestawów mieszanych:

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

Ten kod generuje następujące dane wyjściowe:

```Output
Module ctor initializing based on global instance of class.

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>Zobacz także

[Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
