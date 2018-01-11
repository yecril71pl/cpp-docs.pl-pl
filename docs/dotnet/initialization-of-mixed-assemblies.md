---
title: "Inicjalizacja zestawów mieszanych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e7d192387131ff0eaa04fc366254d7f78a73dd52
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="initialization-of-mixed-assemblies"></a>Inicjalizacja zestawów mieszanych
Przed Visual Studio 2005, biblioteki DLL są kompilowane przy użyciu **/CLR** — opcja kompilatora można w sposób niejednoznaczny zakleszczenie po załadowaniu; ten problem został wywołany mieszanych problem DLL ładowania lub modułu ładującego blokady. Prawie wszystkie z systemem innym niż determinizm została usunięta z mieszanym proces ładowania biblioteki DLL. Istnieje jednak kilka pozostałych scenariusze, dla których moduł ładujący (sposób niejednoznaczny) może wystąpić blokady.
  
 Kod w [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) nie może uzyskać dostępu do środowiska CLR. Oznacza to, że `DllMain` upewnić nie wywołania funkcji zarządzanych, bezpośrednio lub pośrednio; żadnego kodu zarządzanego powinny być zadeklarowane lub zaimplementowana w `DllMain`; i nie wyrzucanie elementów bezużytecznych lub biblioteki automatyczne ładowanie powinno odbywać się w obrębie `DllMain` .  
  
> [!NOTE]
>  Program Visual C++ 2003 podać _vcclrit.h ułatwiające inicjowania biblioteki DLL przy jednoczesnym zmniejszeniu możliwości zakleszczenia. Przy użyciu _vcclrit.h nie jest już konieczne i powoduje, że ostrzeżenia dotyczące zaniechania do wyprodukowania podczas kompilacji. Strategii zalecane jest usunięcie zależności od tego pliku, wykonując kroki w [_vcclrit.h usuwanie przestarzały plik nagłówka](http://msdn.microsoft.com/en-us/7881993e-431d-43e9-8c6d-0d2285a4882d). Mniej idealne rozwiązania obejmują, pomijanie ostrzeżeń, definiując `_CRT_VCCLRIT_NO_DEPRECATE` przed tym _vcclrit.h lub jedynie ignoruje ostrzeżenia dotyczące zaniechania.  
  
## <a name="causes-of-loader-lock"></a>Przyczyny blokady modułu ładującego  
 Wraz z wprowadzeniem platformy .NET istnieją dwa różne mechanizmy ładowania modułu wykonywania (plik EXE lub DLL): jeden dla systemu Windows, jest używana dla modułów niezarządzane, a drugi dla .NET wspólnego języka środowiska uruchomieniowego (CLR) która ładuje zestawów platformy .NET. Mieszane problem podczas ładowania biblioteki DLL koncentruje się wokół modułu ładującego systemu Microsoft Windows.  
  
 Gdy zestawu zawierającego tylko konstrukcje .NET jest ładowany do procesu, moduł ładujący CLR można przeprowadzać wszystkich niezbędnych zadań ładowanie i Inicjowanie samej siebie. Jednak dla zestawów mieszanych, ponieważ zawierają kodu natywnego i danych, modułu ładującego systemu Windows należy użyć również.  
  
 Moduł ładujący systemu Windows gwarantuje, że żaden kod można kod dostępu lub danych w tej bibliotece DLL przed została zainicjowana i że żaden kod nadmiarowo można załadować biblioteki DLL, podczas częściowo został zainicjowany. Aby to zrobić, moduł ładujący systemu Windows używa procesu globalnego sekcja krytyczna (często nazywane "blokady modułu ładującego"), która uniemożliwia niebezpieczny dostęp podczas inicjowania modułu. W związku z tym proces ładowania jest narażony na wiele scenariuszy, w klasycznym zakleszczenia. Dla zestawów mieszanych następujące dwa scenariusze zwiększyć ryzyko zakleszczenia:  
  
-   Pierwsza strona, jeśli użytkownicy próba wykonania funkcji skompilowany na język pośredni firmy Microsoft (MSIL) przytrzymanie blokady modułu ładującego (z `DllMain` lub statyczne inicjatory, na przykład), może to spowodować zakleszczenia. Rozważmy przypadek, w którym funkcja MSIL odwołuje się do typu w zestawie, który nie został załadowany. Środowisko CLR spróbuje automatycznie załadować tego zestawu, które mogą wymagać modułu ładującego systemu Windows do blokowania na blokady modułu ładującego. Ponieważ blokada modułu ładującego jest już w posiadaniu kodu we wcześniejszej części sekwencję wywołań, zakleszczenie wyników. Jednak wykonywania MSIL w obszarze blokady modułu ładującego nie gwarantuje, że zakleszczenie nastąpi, utrudniając zdiagnozować i naprawić tego scenariusza. W pewnych okolicznościach np. gdy typu występującego w odwołaniu biblioteki DLL zawiera nie natywnego konstrukcje i wszystkie jego zależności zawierają nie natywnego konstrukcje Windows modułu ładującego nie jest wymagane do załadowania zestawu .NET, do którego istnieje odwołanie typu. Ponadto wymagany zestaw lub jego zależności mieszanych native/.NET mogą zostały już załadowane przez inny kod. W rezultacie zakleszczenia może być trudna do przewidzenia i może się różnić w zależności od konfiguracji komputera docelowego.  
  
-   Drugie podczas ładowania biblioteki dll w wersjach 1.0 i 1.1 programu .NET Framework, CLR założono, że blokady modułu ładującego nie został zablokowany i wykonać kilka czynności, które nie są prawidłowe w obszarze blokady modułu ładującego. Przy założeniu, że blokada modułu ładującego nie jest używana jest nieprawidłowa założeń dla czysto .NET bibliotek DLL, ale ponieważ mieszanych bibliotek DLL procedury inicjowania macierzystego, wymagają one natywnego modułu ładującego systemu Windows i w związku z tym blokady modułu ładującego. W związku z tym nawet jeśli nie dewelopera próbowano wykonać wszystkie funkcje MSIL podczas inicjowania biblioteki DLL, było nadal mało prawdopodobne niedeterministyczne zakleszczenie w wersjach 1.0 i 1.1 programu .NET Framework.  
  
 Wszystkie z systemem innym niż determinizm została usunięta z mieszanym proces ładowania biblioteki DLL. Zostało to zrobić z tych zmian:  
  
-   Środowisko CLR nie tworzy już false założenia gdy ładowanie mieszanych bibliotek DLL.  
  
-   Inicjowanie niezarządzane i zarządzane odbywa się w dwóch etapach oddzielne. Inicjowanie niezarządzane odbywa się najpierw (za pośrednictwem funkcji DllMain) i odbywa się inicjowanie zarządzanego później za pomocą. Konstrukcja obsługiwane NET o nazwie *.cctor*. Drugie polecenie jest całkowicie niewidoczne dla użytkownika o ile **/Zl** lub **/nodefaultlib** są używane. Zobacz[/nodefaultlib (Ignoruj biblioteki)](../build/reference/nodefaultlib-ignore-libraries.md) i [/Zl (Pomiń domyślną nazwę biblioteki)](../build/reference/zl-omit-default-library-name.md) Aby uzyskać więcej informacji.  
  
 Blokady modułu ładującego nadal może wystąpić, ale teraz występuje odtwarzalnie i wykrycia. Jeśli DllMain zawiera instrukcje MSIL, kompilator generuje ostrzeżenie [C4747 ostrzeżenie kompilatora (poziom 1)](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Ponadto CRT lub CLR próbuje wykryć i zgłoś prób wykonania MSIL w obszarze blokady modułu ładującego. Powoduje wykrywania CRT środowiska uruchomieniowego diagnostyki C Run-Time błąd R6033.  
  
 Pozostałej części niniejszego dokumentu opisano scenariusze pozostałe, dla których MSIL można wykonywać w obszarze blokady modułu ładującego rozwiązania problemu w każdej z tych scenariuszy i techniki debugowania.  
  
## <a name="scenarios-and-workarounds"></a>Scenariusze i rozwiązania  
 Istnieje kilka różnych sytuacji, w których kod użytkownika może zostać uruchomiony MSIL w obszarze blokady modułu ładującego. Deweloper musi zapewnić, że implementacji kodu użytkownika nie jest podejmowana próba wykonania instrukcji MSIL w każdej z tych sytuacji. Poniższe podpunkty opisują wszystkie możliwości z omówienie sposobu rozwiązywania problemów w typowych przypadkach.  
  
-   `DllMain`  
  
-   Statyczne inicjatory  
  
-   Dostarczone przez użytkownika funkcji wpływających na uruchamiania  
  
-   Niestandardowe ustawienia regionalne  
  
### <a name="dllmain"></a>DllMain  
 `DllMain` Funkcji jest zdefiniowane przez użytkownika punkt wejścia biblioteki DLL. Jeśli użytkownik określi, w przeciwnym razie `DllMain` jest wywoływane każdorazowo proces lub wątek dołącza do lub odłączenie od zawierającego biblioteki DLL. Ponieważ to wywołanie może wystąpić, dopóki blokada modułu ładującego jest utrzymywana, dostarczone przez użytkownika nie `DllMain` funkcji powinny zostać skompilowane do MSIL. Ponadto, żadna funkcja w drzewie wywołań początek w `DllMain` zostać skompilowane do MSIL. Aby rozwiązać problemy, blok kodu, który definiuje `DllMain` powinny być modyfikowane za pomocą #pragma `unmanaged`. Należy dokładnie takie same dla każdej funkcji który `DllMain` wywołania.  
  
 W przypadkach, gdy te funkcje należy wywołać funkcję, która wymaga wykonania MSIL dla innych kontekstach wywoływania strategii dublowania może służyć których są tworzone jednocześnie .NET, jak i natywną wersję tej samej funkcji.  
  
 Alternatywnie Jeśli `DllMain` nie jest wymagana lub jeśli nie trzeba być wykonywane w ramach modułu ładującego zablokować, dostarczane przez użytkownika `DllMain` można usunąć wdrożenia, który będzie usunąć ten problem.  
  
 Jeśli DllMain podejmuje próbę wykonania MSIL bezpośrednio, [C4747 ostrzeżenie kompilatora (poziom 1)](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) spowoduje. Jednak kompilator nie może wykryć przypadków, gdy wywołuje funkcję DllMain w innym module, który z kolei podejmuje próbę wykonania MSIL.  
  
 Aby uzyskać więcej informacji na temat tego scenariusza, zobacz "Przeszkód do diagnozowania".  
  
### <a name="initializing-static-objects"></a>Inicjowanie obiektów statycznych  
 Inicjowanie statyczne obiektów może spowodować zakleszczenie Jeśli wymagana jest dynamiczny inicjatora. W przypadku prostych przypadkach, takich jak kiedy zmienna statyczna jest po prostu przypisać do wartości znane w czasie kompilacji nie dynamiczna Inicjalizacja wymagane jest, nie istnieje ryzyko zakleszczenia. Jednak zmienne statyczne zainicjowane przez wywołania funkcji, wywołania konstruktora lub wyrażeń, które nie można obliczyć w kompilacji czasu wymaga kod do wykonania podczas inicjowania modułu.  
  
 Poniższy kod przedstawia przykłady inicjatorów statycznych, które wymagają dynamicznego inicjowania: wywołanie funkcji, konstrukcji obiektów i inicjowania wskaźnika. (Te przykłady nie są statyczne, ale są zakłada, że ma zostać zdefiniowana w zakresie globalnym, który ma ten sam efekt).  
  
```  
// dynamic initializer function generated  
int a = init();  
CObject o(arg1, arg2);    
CObject* op = new CObject(arg1, arg2);  
```  
  
 To ryzyko zakleszczenia zależy od tego, czy moduł zawierający jest skompilowana przy użyciu **/CLR** , zostanie wykonany MSIL. W szczególności jeśli zmienna statyczna jest kompilowany bez **/CLR** (lub znajduje się w #pragma `unmanaged` blok), a inicjator dynamiczne wymagane zainicjować powoduje wykonanie instrukcji MSIL, zakleszczenie mogą występować. Wynika to z faktu, modułów skompilowany bez **/CLR**, inicjowanie zmienne statyczne odbywa się za pośrednictwem funkcji DllMain. Z kolei zmienne statyczne skompilowane z **/CLR** są inicjowane przez .cctor, po zakończeniu etapu niezarządzane inicjowania i zostało zwolnione blokady modułu ładującego.  
  
 Istnieje wiele rozwiązań zakleszczenie spowodowane dynamiczna Inicjalizacja zmienne statyczne (w sposób uporządkowane około czas wymagany do rozwiązany):  
  
-   Plik źródłowy zawierający statyczna zmienna może być kompilowana przy użyciu **/CLR**.  
  
-   Wszystkie funkcje wywoływane przez zmienną statyczne mogą być kompilowane do kodu natywnego za pomocą #pragma `unmanaged` dyrektywy.  
  
-   Ręcznie sklonować kod, który zmienna statyczna zależy, zapewniając jednocześnie .NET, jak i natywną wersję o różnych nazwach. Deweloperzy można wywołać natywną wersję z natywnego statyczne inicjatory i wywołuje wersji platformy .NET w innym miejscu.  
  
### <a name="user-supplied-functions-affecting-startup"></a>Dostarczone przez użytkownika funkcji wpływających na uruchamiania  
 Istnieje kilka funkcji dostarczone przez użytkownika, na których biblioteki są zależne dla inicjowania podczas uruchamiania. Na przykład gdy globalnie takich jak przeładowanie operatorów w języku C++ `new` i `delete` operatorów, wersje dostarczane przez użytkownika są używane wszędzie, takich jak inicjowanie standardowa biblioteka C++ i zniszczenia. W związku z tym standardowa biblioteka C++ i dostarczane przez użytkownika statyczne inicjatory wywoła wszelkie dostarczane przez użytkownika wersje tych operatorów.  
  
 Jeśli wersje dostarczane przez użytkownika są skompilowane do MSIL, te inicjatory zostanie próba do wykonywania instrukcji MSIL, dopóki blokada modułu ładującego jest utrzymywana. — Funkcja malloc dostarczone przez użytkownika ma takie same skutki. Aby rozwiązać ten problem, żadnego z tych przeciążenia lub definicji dostarczone przez użytkownika muszą zostać zaimplementowane jako kod natywny za pomocą #pragma `unmanaged` dyrektywy.  
  
 Aby uzyskać więcej informacji na temat tego scenariusza, zobacz "Przeszkód do diagnozowania".  
  
### <a name="custom-locales"></a>Niestandardowe ustawienia regionalne  
 Jeśli użytkownik udostępnia niestandardowych globalnych ustawień regionalnych, tych ustawień regionalnych będzie używany dla wszystkich przyszłych strumieni We/Wy, w tym te, które są inicjowane statycznie inicjowania. Jeśli ten obiekt globalnych ustawień regionalnych jest skompilowane do MSIL, funkcji Członkowskich obiektu ustawień regionalnych skompilowane do MSIL może wywołać dopóki blokada modułu ładującego jest utrzymywana.  
  
 Dostępne są trzy opcje dotyczące rozwiązywania tego problemu:  
  
 Pliki źródłowe, zawierający wszystkie definicje globalnej strumień we/wy może być kompilowana przy użyciu **/CLR** opcji. Uniemożliwi to ich statyczne inicjatory z są wykonywane w ramach blokady modułu ładującego.  
  
 Definicje funkcji niestandardowych ustawień regionalnych można skompilowanych do natywnego kodu za pomocą #pragma `unmanaged` dyrektywy.  
  
 Unikaj umieszczania ustawienie globalne ustawienia regionalne do niestandardowych ustawień regionalnych po zwolnieniu blokady modułu ładującego. Należy jawnie skonfigurować strumieni We/Wy utworzone podczas inicjowania z niestandardowych ustawień regionalnych.  
  
## <a name="impediments-to-diagnosis"></a>Przeszkody diagnostyki  
 W niektórych przypadkach jest trudne do wykrycia źródła zakleszczenia. Poniższe podpunkty omówiono konfigurowanie tych scenariuszy i sposoby obejścia tych problemów.  
  
### <a name="implementation-in-headers"></a>Implementacja w nagłówkach  
 W przypadku wybierz implementacji funkcji wewnątrz pliki nagłówkowe skomplikować diagnostyki. Wbudowane funkcje i kod szablonu wymagają określenia funkcji w pliku nagłówka.  Język C++ Określa jedną regułę definicji wymusza implementacje wszystkich funkcji o takiej samej nazwie semantycznie równoważne. W związku z tym konsolidatora C++ nie muszą wprowadzać uwagi użytkownika podczas scalania obiektów pliki, których zduplikowane implementacji danej funkcji.  
  
 Przed Visual Studio 2005 konsolidator po prostu wybiera największy te semantycznie równoważne definicje, aby pomieścić deklaracje do przodu i scenariuszy stosowania optymalizacji różnych opcji dla plików źródłowych różnych. Spowoduje to utworzenie problemu z macierzystego/.NET mieszanych bibliotek DLL.  
  
 Ponieważ ten sam nagłówek może być włączone zarówno w plikach CPP, z **/CLR** włączone i wyłączone, lub #include można ich opakować wewnątrz #pragma `unmanaged` bloku, istnieje możliwość MSIL i macierzyste wersje funkcji, które zapewniają implementacje w nagłówkach. Natywnych implementacji i MSIL ma semantykę różną względem inicjowania w obszarze blokady modułu ładującego, które skutecznie narusza reguły jednej definicji. W związku z tym gdy konsolidator wybierze największa implementacja, go może wybierz wersję MSIL funkcję, nawet jeśli jawnie została skompilowana do kodu macierzystego w innym miejscu przy użyciu dyrektywy #pragma niezarządzanych. Aby upewnić się, że wersja MSIL szablon lub wewnętrznej funkcji nigdy nie jest wywoływana w obszarze blokady modułu ładującego, muszą zostać zmodyfikowane w każdej definicji co takich funkcji o nazwie blokady modułu ładującego z #pragma `unmanaged` dyrektywy. Jeśli plik nagłówka pochodzi z innej firmy, najprostszym sposobem, aby to osiągnąć jest wypychania i pop dyrektywa #pragma niezarządzanego wokół #include — dyrektywa ataku pliku nagłówka. (Zobacz [zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) np.) Ta strategia nie będzie działać dla nagłówków zawierających innego kodu, który należy bezpośrednio wywoływać interfejsów API architektury .NET.  
  
 Dla wygody użytkowników zajmujących się blokady modułu ładującego wybierze konsolidator implementacji native za pośrednictwem zarządzanych przedstawionej obu.  Dzięki temu można uniknąć powyższe problemy.  Istnieją dwa wyjątki od tej reguły w tej wersji z powodu dwóch nierozwiązane problemy z kompilatorem:  
  
-   Wywołanie jest elementem śródwierszowym funkcja jest za pomocą wskaźnika funkcji globalnej statycznych.  Ten scenariusz jest szczególnie ważne, ponieważ funkcje wirtualne są wywoływane za pośrednictwem wskaźników funkcji globalnych.  Na przykład  
  
```  
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
  
-   Celem Itanium kompilacji jest usterki w implementacji wskaźników funkcji.  W poprzednim przykładzie Jeśli myObject_p zostały zdefiniowane lokalnie wewnątrz during_loaderlock(), połączenie może być rozpoznana jako zarządzaną implementację.  
  
### <a name="diagnosing-in-debug-mode"></a>Diagnozowanie w trybie debugowania  
 Wszystkie diagnozować blokady modułu ładującego, który problemów należy zrobić z kompilacji debugowania. Wersja kompilacji nie może utworzyć diagnostyki i optymalizacje wykonywane w trybie wersji może maskować niektóre MSIL w scenariuszach blokady modułu ładującego.  
  
## <a name="how-to-debug-loader-lock-issues"></a>Debugowanie problemów blokady modułu ładującego  
 Dane diagnostyczne generowany przez środowisko CLR po wywołaniu funkcji MSIL powoduje, że CLR wstrzymania wykonywania. Z kolei powoduje debugera trybu mieszanego Visual C++, również zostanie zawieszona, podczas uruchamiania obiektu debugowanego w procesie. Jednakże podczas dołączania do procesu, nie jest możliwość uzyskania zarządzany stos wywołań dla obiekt debugowany przy użyciu mieszanych debugera.  
  
 Aby zidentyfikować określoną funkcję MSIL, która została wywołana w obszarze blokady modułu ładującego, deweloperzy powinien wykonaj następujące kroki:  
  
1.  Upewnij się, że dostępne są symbole dla biblioteki mscoree.dll i mscorwks.dll.a;a;pierwsza.  
  
     Można to zrobić na dwa sposoby. Po pierwsze można dodać do ścieżki wyszukiwania symboli PDB dla biblioteki mscoree.dll i mscorwks.dll.a;a;pierwsza. Aby to zrobić, Otwórz okno dialogowe Opcje ścieżki wyszukiwania symboli. (W menu Narzędzia kliknij przycisk Opcje. W lewym okienku okna dialogowego Opcje Otwórz węzeł debugowanie i kliknij symbole.) Dodaj ścieżkę do plików PDB mscoree.dll i mscorwks.dll.a;a;pierwsza do listy wyszukiwania. Te pliki PDB są instalowane na % VSINSTALLDIR%\SDK\v2.0\symbols. Kliknij przycisk OK.  
  
     Po drugie pliki PDB dla biblioteki mscoree.dll i mscorwks.dll.a;a;pierwsza można pobrać z serwera symboli firmy Microsoft. Aby skonfigurować serwer symboli, Otwórz okno dialogowe Opcje ścieżki wyszukiwania symboli. (W menu Narzędzia kliknij przycisk Opcje. W lewym okienku okna dialogowego Opcje Otwórz węzeł debugowanie i kliknij symbole.) Dodaj następującą ścieżkę wyszukiwania do listy wyszukiwania: http://msdl.microsoft.com/download/symbols. Dodaj katalog pamięci podręcznej symboli do pola tekstowego pamięci podręcznej serwera symboli. Kliknij przycisk OK.  
  
2.  Ustaw tryb debugowania wyłącznie natywnego trybu.  
  
     Aby to zrobić, otwórz siatki właściwości projektu startowego w rozwiązaniu. W obszarze właściwości konfiguracji poddrzewo wybierz węzeł debugowania. Ustaw dla pola typu debugowania wyłącznie natywnego.  
  
3.  Uruchom debuger (F5).  
  
4.  Gdy **/CLR** diagnostyczne jest generowany, kliknij przycisk Ponów próbę, a następnie kliknij przycisk podziału.  
  
5.  Otwórz okno stosu wywołań. (Z menu Debugowanie kliknij system Windows, a następnie stos wywołań). Jeśli naruszeń `DllMain` lub statycznego inicjatora jest identyfikowany z zieloną strzałką. Jeśli nie określono funkcji ataku, poniższe kroki należy go znaleźć.  
  
6.  Otwórz okno natychmiastowe (z menu Debugowanie kliknij system Windows, a następnie Immediate).  
  
7.  W oknie bezpośrednim można załadować usługi do debugowania SOS wpisz .load sos.dll.  
  
8.  Typ! dumpstack do okna bezpośredniego, aby uzyskać pełną listę wewnętrznej **/CLR** stosu.  
  
9. Wyszukaj pierwszego wystąpienia (znajdujący się najbliżej spodzie stosu) albo _CorDllMain (Jeśli `DllMain` powoduje, że problem) lub _VTableBootstrapThunkInitHelperStub lub GetTargetForVTableEntry (Jeśli inicjator statyczny powoduje, że problem).  Wpis stosu poniżej tego wywołania jest wywołania MSIL zaimplementowana funkcja, która nastąpiła próba wykonania w obszarze blokady modułu ładującego.  
  
10. Przejdź do pliku źródłowego i numer zidentyfikowanego w kroku 9 i prawidłowe wiersza problem przy użyciu scenariusze i rozwiązania opisane w sekcji scenariuszy.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje, jak uniknąć blokady modułu ładującego przenosząc kodu z funkcji DllMain do konstruktora obiektu globalnego.  
  
 W tym przykładzie jest globalnego obiektu zarządzanego którego konstruktor zawiera obiekt zarządzany, który pierwotnie w funkcji DllMain. Druga część tego przykładu odwołuje się do zestawu, tworzenia wystąpienia obiektu zarządzanego można wywołać konstruktora modułu, która obsługuje inicjowania.  
  
### <a name="code"></a>Kod  
  
```  
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
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
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
  
### <a name="output"></a>Dane wyjściowe  
  
```  
Module ctor initializing based on global instance of class.  
  
Test called so linker does not throw away unused object.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)