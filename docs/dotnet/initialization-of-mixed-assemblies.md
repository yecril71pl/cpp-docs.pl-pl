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
ms.openlocfilehash: 1f4ea7f5cfc6e99390c93ba9c2beadc46fce8584
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339042"
---
# <a name="initialization-of-mixed-assemblies"></a>Inicjalizacja zestawów mieszanych

Programiści Windows zawsze musi być ostrożnym blokady modułu ładującego podczas uruchamiania kodu podczas `DllMain`. Istnieją jednak pewne dodatkowe kwestie, które dochodzą do głosu podczas pracy z C++zestawy mieszane/CLR.

Kod w ramach [DllMain](/windows/desktop/Dlls/dllmain) nie może uzyskać dostępu do środowiska CLR. Oznacza to, że `DllMain` powinien sprawia, że żadne wywołania do funkcji zarządzanej, bezpośrednio lub pośrednio; bez kodu zarządzanego powinny być zadeklarowane lub zaimplementowane w `DllMain`; i nie wyrzucania elementów bezużytecznych lub biblioteki automatyczne ładowanie powinno odbywać się w ramach `DllMain` .

## <a name="causes-of-loader-lock"></a>Przyczyny blokady modułu ładującego

Wraz z wprowadzeniem platformy .NET, istnieją dwa odrębne mechanizmy ładowania modułu wykonywania (EXE lub DLL): jeden dla Windows, która jest używana dla modułów niezarządzanych, a drugi dla platformy .NET języka wspólnego środowiska uruchomieniowego (CLR), która ładuje zestawy .NET. Mieszane problem podczas ładowania biblioteki DLL koncentruje się wokół modułu ładującego systemu operacyjnego Windows firmy Microsoft.

Gdy zestaw zawierający tylko .NET konstrukcji jest ładowany do procesu, moduł ładujący CLR można wykonywać wszystkie niezbędne zadania, ładowanie i Inicjowanie sam. Jednak dla zestawów mieszanych, ponieważ zawierają natywnego kodu i danych, moduł ładujący Windows należy użyć także.

Moduł ładujący Windows gwarantuje, czy bez kodu można kod dostępu lub danych w tej bibliotece DLL, zanim została zainicjowana i, bez kodu nadmiarowo można załadować biblioteki DLL, a częściowo jest inicjowany. Aby to zrobić, moduł ładujący Windows używa globalnego procesu sekcję krytyczną (często nazywane "blokady modułu ładującego"), które blokują dostęp niebezpiecznych podczas inicjowania modułu. W rezultacie proces ładowania jest narażony na wiele scenariuszy klasycznego zakleszczenia. Dla zestawów mieszanych następujące dwa scenariusze zwiększają ryzyko zakleszczenia:

- Pierwsze, jeśli użytkownicy spróbują wykonać funkcjach skompilowanych do języka Microsoft intermediate language (MSIL), przytrzymanie blokady modułu ładującego (z `DllMain` lub statyczne inicjatory, na przykład), może to spowodować zakleszczenia. Należy rozważyć przypadek, w którym funkcja MSIL odwołuje się do typu w zestawie, który nie został załadowany. Środowisko CLR spróbuje automatycznie załadować tego zestawu, które mogą wymagać moduł ładujący Windows, aby zablokować na blokady modułu ładującego. Ponieważ blokada modułu ładującego jest już posiadanych przez kodu we wcześniejszej części sekwencję wywołań, spowoduje zakleszczenia. Jednak wykonanie MSIL w ramach blokady modułu ładującego nie gwarantuje, że zakleszczenie nastąpi, dzięki czemu ten scenariusz jest trudny do zdiagnozowania i rozwiązania. W pewnych okolicznościach np. gdy zawiera biblioteki DLL, do którego istnieje odwołanie typu nie natywnego konstrukcje i wszystkie jego zależności zawierają nie natywnego konstrukcje Windows modułu ładującego nie jest wymagane do załadowania zestawu .NET typu odwołania. Ponadto wymagany zestaw lub jego zależności mieszane native/.NET może zostały już załadowane przez inny kod. W związku z tym zakleszczenia mogą być trudne do przewidzenia i mogą się różnić w zależności od konfiguracji komputera docelowego.

- Po drugie podczas ładowania biblioteki dll w wersjach 1.0 i 1.1 programu .NET Framework, CLR zakłada, że że blokady modułu ładującego nie został zablokowany, a następnie wykonać kilka czynności, które są nieprawidłowe w ramach blokady modułu ładującego. Przy założeniu, że blokada modułu ładującego nie jest używana jest prawidłowy założeń czysto bibliotek DLL platformy .NET, ale ponieważ procedury inicjowania w natywnych są wykonywane w mieszanych bibliotek DLL, wymagają one natywnego modułu ładującego Windows i w związku z tym blokady modułu ładującego. W związku z tym nawet wtedy, gdy deweloper nie próbowano wykonać wszystkie funkcje MSIL podczas inicjowania biblioteki DLL, było nadal niewielkie prawdopodobieństwo niedeterministyczne zakleszczenie w wersjach 1.0 i 1.1 programu .NET Framework.

Wszystkie niedeterminizmu został usunięty z mieszanych bibliotek DLL, proces ładowania. To było wykonywane za pomocą tych zmian:

- Środowisko CLR nie jest już sprawia, że założenia false, gdy ładowanie mieszanych bibliotek DLL.

- Inicjowanie zarządzane i niezarządzane odbywa się w dwóch etapach odrębne i niezależne. Niezarządzane inicjowanie odbywa się najpierw (za pośrednictwem funkcji DllMain) i odbywa się inicjowanie zarządzanego później za pomocą. Obsługiwane NET konstrukcja o nazwie *.cctor*. Nie jest całkowicie niewidoczne dla użytkownika o ile nie **/Zl** lub **/nodefaultlib** są używane. Zobacz[/nodefaultlib (Ignoruj biblioteki)](../build/reference/nodefaultlib-ignore-libraries.md) i [/Zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) Aby uzyskać więcej informacji.

Blokady modułu ładującego jest nadal możliwe, ale teraz występuje odtwarzalnie i wykrycia. Jeśli `DllMain` zawiera instrukcje MSIL, kompilator generuje ostrzeżenie [ostrzeżenie kompilatora (poziom 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Ponadto CRT lub środowiska CLR podejmie próbę wykrycia i zgłoś prób wykonania MSIL w ramach blokady modułu ładującego. Wykrywanie CRT wyników w środowisku uruchomieniowym diagnostycznych R6033 błąd czasu wykonywania C.

W pozostałej części tego dokumentu opisano scenariusze pozostałych, dla których MSIL można wykonać w ramach blokady modułu ładującego rozwiązania problemu pod każdym z tych scenariuszy i techniki debugowania.

## <a name="scenarios-and-workarounds"></a>Scenariusze i rozwiązania

Istnieje kilka różnych sytuacji, w których kod użytkownika mogą wykonywać MSIL w ramach blokady modułu ładującego. Deweloper musi zapewnić, że implementacja kodu użytkownika nie jest podejmowana próba wykonania instrukcji MSIL pod każdym z tych sytuacji. Poniższe podsekcje opisano wszystkie możliwości dzięki dyskusję na temat sposobu rozwiązywania problemów w najbardziej typowe przypadki.

### <a name="dllmain"></a>DllMain

`DllMain` Funkcja jest punktem wejścia zdefiniowane przez użytkownika dla biblioteki DLL. Chyba że użytkownik określi, w przeciwnym razie `DllMain` jest wywoływana za każdym razem, gdy proces lub wątek dołącza do lub odłącza się od zawierającego biblioteki DLL. Ponieważ to wywołanie może wystąpić, gdy utrzymania blokady modułu ładującego, dostarczone przez użytkownika nie `DllMain` funkcja powinna zostać skompilowane do MSIL. Ponadto, żadna funkcja w drzewie wywołań, dostęp do konta root na `DllMain` można skompilować do MSIL. Aby rozwiązać problemy w tym miejscu blok kodu, który definiuje `DllMain` powinny być modyfikowane przy użyciu #pragma `unmanaged`. Taki sam powinno odbywać się dla każdej funkcji, która `DllMain` wywołania.

W przypadkach, w którym tych funkcji, należy wywołać funkcję, która wymaga implementacji MSIL dla innych kontekstach wywoływania strategii dublowania może służyć tworzona .NET i natywną wersję tej samej funkcji.

Alternatywnie Jeśli `DllMain` nie jest wymagane lub jeśli nie trzeba być wykonywane w ramach modułu ładującego zablokować, dostarczone przez użytkownika `DllMain` można usunąć wdrożenia, który zostanie całkowicie wyeliminować problem.

Jeśli DllMain próbuje wykonać bezpośrednio MSIL [ostrzeżenie kompilatora (poziom 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) spowoduje. Jednak kompilator nie może wykryć przypadki, w którym DllMain wywołuje funkcję w innym module, który z kolei podejmuje próbę wykonania MSIL.

Aby uzyskać więcej informacji na temat tego scenariusza, zobacz "Przeszkody do diagnostyki".

### <a name="initializing-static-objects"></a>Inicjowanie obiektów statycznych

Inicjowanie obiektów statycznych może spowodować zakleszczenia, jeśli dynamiczny inicjator jest wymagana. Dla prostych przypadkach, takich jak kiedy zmienna statyczna jest po prostu przypisać do wartości znany w czasie kompilacji nie dynamiczna Inicjalizacja wymagane jest, więc nie występuje ryzyko zakleszczenia. Jednak statyczne zmienne inicjowane przez wywołania funkcji, wywołania konstruktora lub wyrażeń, które nie mogą być obliczane w kompilacji czas wszystkie wymagane do wykonania podczas inicjowania modułu kodu.

Poniższy kod pokazuje przykłady statyczne inicjatory, które wymagają dynamicznego inicjowania: wywołanie funkcji, konstrukcji obiektów i inicjowania wskaźnika. (Te przykłady nie są statyczne, ale są zakłada się, że można zdefiniować w zakresie globalnym, która ma ten sam efekt).

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

To ryzyko zakleszczenia zależy od tego, czy zawierające moduł został skompilowany z **/CLR** i zostanie wykonany MSIL. W szczególności jeśli zmienna statyczna jest kompilowany bez **/CLR** (lub znajduje się w #pragma `unmanaged` blok), i dynamiczny inicjator wymagane to inicjalizacji, jej wyniki podczas wykonywania instrukcji MSIL, mogą występować zakleszczenia. Jest to spowodowane dla modułów skompilowanych bez **/CLR**, Inicjalizacja zmiennych statycznych odbywa się przez funkcji DllMain. Z kolei zmienne statyczne skompilowany przy użyciu **/CLR** są inicjowane przy .cctor, po zakończeniu na etapie inicjowania niezarządzanych i udostępnieniu blokady modułu ładującego.

Istnieje kilka rozwiązań zakleszczenie spowodowane dynamiczna Inicjalizacja zmiennych statycznych (rozmieszczone około według czasu wymaganego do problemu):

- Plik źródłowy zawierający zmienna statyczna może być skompilowana przy użyciu **/CLR**.

- Wszystkie funkcje wywoływane przez zmienną statyczną, może być kompilowane do kodu natywnego za pomocą #pragma `unmanaged` dyrektywy.

- Ręcznie sklonować kod, który zmienna statyczna zależy, zapewniając .NET i natywnego wersji pod różnymi nazwami. Deweloperzy mogą następnie wywołać natywnej wersji z natywnych statyczne inicjatory i wywołać wersji programu .NET w innym miejscu.

### <a name="user-supplied-functions-affecting-startup"></a>Dostarczone przez użytkownika funkcje wpływające na uruchamiania

Istnieje kilka funkcji dostarczone przez użytkownika, od których bibliotek zależą inicjowania podczas uruchamiania. Na przykład w przypadku globalnie przeciążania operatory w języku C++, takich jak `new` i `delete` operatorów, wersje dostarczone przez użytkownika są używane wszędzie, w tym w standardowej biblioteki języka C++ inicjowania i niszczenia. W rezultacie standardowej biblioteki języka C++ i podanych przez użytkownika statyczne inicjatory wywoła wszystkie dostarczone przez użytkownika wersje tych operatorów.

Jeśli wersje dostarczone przez użytkownika są skompilowane do MSIL, można wykonać instrukcji MSIL, dopóki blokada modułu ładującego jest utrzymywana podjęto jest te inicjatory. Użytkownik podał `malloc` ma takie same skutki. Aby rozwiązać ten problem, żadnego z tych przeciążeń lub definicji dostarczone przez użytkownika musi zostać wdrożony jako kodu natywnego za pomocą #pragma `unmanaged` dyrektywy.

Aby uzyskać więcej informacji na temat tego scenariusza, zobacz "Przeszkody do diagnostyki".

### <a name="custom-locales"></a>Niestandardowe ustawienia regionalne

Jeśli użytkownik poda niestandardowe globalnych ustawień regionalnych, tych ustawień regionalnych będą używane do inicjowania wszystkich przyszłych strumieniach we/wy, w tym te, które są statycznie zainicjowane. Jeśli ten obiekt globalnych ustawień regionalnych jest kompilowany na język MSIL, funkcji elementów członkowskich obiektu ustawień regionalnych skompilowane do MSIL może być wywoływane podczas utrzymania blokady modułu ładującego.

Dostępne są trzy opcje dotyczące rozwiązywania tego problemu:

Pliki źródłowe, zawierający wszystkie definicje globalnego strumienia we/wy może być skompilowana przy użyciu **/CLR** opcji. Uniemożliwi to ich statyczne inicjatory zostanie wykonywany w ramach blokady modułu ładującego.

Niestandardowe ustawienia regionalne definicje funkcji może być kompilowane do kodu natywnego za pomocą #pragma `unmanaged` dyrektywy.

Powstrzymanie się od konfigurowania niestandardowych ustawień regionalnych jako globalne ustawienia regionalne do momentu po wydaniu blokady modułu ładującego. Następnie skonfiguruj jawnie strumieniach we/wy utworzone podczas inicjowania przy użyciu niestandardowych ustawień regionalnych.

## <a name="impediments-to-diagnosis"></a>Przeszkody w celu diagnostyki

W niektórych przypadkach jest trudne do wykrycia źródła zakleszczenia. Poniższe podsekcje omówiono te scenariusze i sposoby obejścia tych problemów.

### <a name="implementation-in-headers"></a>Implementacja w nagłówkach

W przypadku wybierz implementacje funkcji w plikach nagłówkowych skomplikować diagnostyki. Funkcje śródwierszowe a kod szablonu wymaga określenia funkcji w pliku nagłówkowym.  Język C++ określa reguły jednej definicji, co zmusza wszystkich implementacjach funkcji o tej samej nazwie semantycznie równoważne. W związku z tym konsolidatora C++ nie należy wprowadzać żadnych szczególnych kwestii podczas scalania plików obiektu, które mają zduplikowane implementacji danej funkcji.

Przed Visual Studio 2005 konsolidator po prostu wybiera największy z tymi definicjami semantycznie równoważne, aby pomieścić deklaracje przechodzenia do przodu i scenariuszy stosowania optymalizacji różne opcje dla innych plików źródłowych. Spowoduje to utworzenie problemu z mieszanym native/.NET biblioteki dll.

Ponieważ ten sam nagłówek może być uwzględniane zarówno przez pliki języka C++ z **/CLR** włączonych i wyłączonych, lub #include może zostać zawinięty wewnątrz #pragma `unmanaged` bloku, można mieć zarówno MSIL, jak i natywne wersje funkcji, które zapewniają implementacje w nagłówkach. MSIL i implementacji mają różną semantykę, w odniesieniu do inicjowania w ramach blokady modułu ładującego, które skutecznie narusza reguły jednej definicji. W związku z tym gdy konsolidator wybierze największa implementacja, go wybrać wersji MSIL w funkcji, nawet wtedy, gdy jawnie został skompilowany do kodu macierzystego, gdzie indziej przy użyciu dyrektywy #pragma niezarządzanych. Aby upewnić się, że MSIL wersję szablonu lub funkcji śródwierszowej. nigdy nie jest wywoływana w ramach blokady modułu ładującego, co definicji każdej takich funkcji o nazwie blokady modułu ładującego musi można modyfikować za pomocą #pragma `unmanaged` dyrektywy. Jeśli plik nagłówkowy jest w innej, najprostszym sposobem osiągnięcia tego jest pop niezarządzanych — dyrektywa #pragma wokół i wypychania #include — dyrektywa powodujący problemy pliku nagłówka. (Zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) np.) Ta strategia nie będzie działać dla nagłówków zawierających innego kodu, który trzeba bezpośrednio wywoływać interfejsy API platformy .NET.

Dla wygody użytkowników zajmujących się blokady modułu ładującego wybierze konsolidator natywnych implementacji za pośrednictwem zarządzanej umieszczeniem zarówno. Umożliwia to uniknięcie powyższe problemy. Istnieją jednak dwa wyjątki związane z regułą w tej wersji z powodu dwóch nierozwiązane problemy za pomocą kompilatora:

- Wywołanie jest wbudowany funkcja jest za pomocą wskaźnika globalnych funkcji statycznych. Ten scenariusz jest szczególnie istotne, ponieważ wirtualne funkcje są wywoływane za pomocą wskaźników funkcji globalnych. Na przykład

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

Wszystkie ich diagnozowania blokady modułu ładującego, problemy, które należy wykonać przy użyciu kompilacji debugowania. Kompilacji wydania nie może tworzyć diagnostyczne i optymalizacje wykonywane w trybie wersji może maskować część MSIL w scenariuszach blokady modułu ładującego.

## <a name="how-to-debug-loader-lock-issues"></a>Jak debugować problemy blokady modułu ładującego

Diagnostyka, generowany przez środowisko CLR, po wywołaniu funkcji MSIL powoduje, że CLR w celu wstrzymania wykonywania. Z kolei powoduje debuger trybu mieszanego Visual C++, również zostać zawieszone, podczas uruchamiania obiektu debugowanego w procesie. Jednak podczas dołączania do procesu, prawdopodobnie nie można uzyskać zarządzanego stosu wywołań dla obiektu debugowanego przy użyciu mieszany debuger.

Aby zidentyfikować konkretną funkcję MSIL, która została wywołana w ramach blokady modułu ładującego, deweloperzy powinny wykonaj następujące czynności:

1. Upewnij się, że dostępne są symbole dla mscoree.dll i mscorwks.dll.

   Można to zrobić na dwa sposoby. Po pierwsze pliki PDB dla mscoree.dll i mscorwks.dll można dodać do ścieżki wyszukiwania symboli. Aby to zrobić, Otwórz okno dialogowe Opcje ścieżki wyszukiwania symboli. (Z **narzędzia** menu, wybierz **opcje**. W okienku po lewej stronie **opcje** po otwarciu okna dialogowego **debugowanie** węzeł i wybierz polecenie **symbole**.) Dodaj ścieżkę do plików PDB mscoree.dll i mscorwks.dll do listy wyszukiwania. Te pliki PDB są instalowane na % VSINSTALLDIR%\SDK\v2.0\symbols. Wybierz **OK**.

   Po drugie pliki PDB dla mscoree.dll i mscorwks.dll można pobrać z serwera symboli firmy Microsoft. Aby skonfigurować serwer symboli, Otwórz okno dialogowe Opcje ścieżki wyszukiwania symboli. (Z **narzędzia** menu, wybierz **opcje**. W okienku po lewej stronie **opcje** po otwarciu okna dialogowego **debugowanie** węzeł i wybierz polecenie **symbole**.) Dodaj następującą ścieżkę wyszukiwania do listy wyszukiwania: http://msdl.microsoft.com/download/symbols. Dodaj katalog pamięci podręcznej symboli do pola tekstowego pamięci podręcznej serwera symboli. Wybierz **OK**.

1. Ustaw tryb debugera w trybie tylko do natywnych.

   Aby to zrobić, otwórz **właściwości** siatka projektu startowego w rozwiązaniu. Wybierz **właściwości konfiguracji** > **debugowania**. Ustaw **typ debugera** do **wyłącznie natywnego**.

1. Uruchom debuger (F5).

1. Gdy **/CLR** diagnostyki jest generowany, wybierz polecenie **ponów próbę wykonania** , a następnie wybierz **Przerwij**.

1. Otwórz okno stosu wywołań. (Na pasku menu wybierz **debugowania** > **Windows** > **stos wywołań**.) Naruszeń `DllMain` lub statycznego inicjatora jest identyfikowany za pomocą zieloną strzałkę. Jeśli funkcja naruszającym nie zostanie zidentyfikowany, poniższe kroki należy go znaleźć.

1. Otwórz **bezpośrednie** okna (na pasku menu wybierz **debugowania** > **Windows** > **bezpośrednie**.)

1. Wpisz sos.dll .load do **bezpośrednie** okna, aby załadować usługi do debugowania SOS.

1. Typ! dumpstack do **bezpośrednie** okna, aby uzyskać pełną listę wewnętrzny **/CLR** stosu.

1. Wyszukaj pierwszego wystąpienia (znajdujący się najbliżej spodzie stosu) albo _cordllmain — (Jeśli `DllMain` powoduje problemy) lub _VTableBootstrapThunkInitHelperStub lub GetTargetForVTableEntry (jeśli statycznego inicjatora powoduje, że problem). Wpis stosu tuż poniżej tego wywołania jest wywołania MSIL zaimplementowana funkcja, która podjęto próbę wykonania w ramach blokady modułu ładującego.

1. Przejdź do pliku źródłowego i numer zidentyfikowany w poprzednim kroku i poprawne wiersza, problem za pomocą scenariusze i rozwiązania opisane w sekcji scenariuszy.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje, jak uniknąć blokady modułu ładującego, przenosząc kodu z `DllMain` do konstruktora obiektów globalnych.

W tym przykładzie jest globalne obiektu zarządzanego, której Konstruktor zawiera obiektu zarządzanego, który został opublikowany w `DllMain`. Druga sekcja w tym przykładzie odwołuje się do zestawu, tworzenia wystąpienia obiektu zarządzanego, można wywołać konstruktora modułu, która obsługuje inicjowania.

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

W tym przykładzie przedstawiono problemy w inicjowanie zestawów mieszanych:

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
