---
title: "-GS (Sprawdzanie zabezpieczeń bufora) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
dev_langs: C++
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
caps.latest.revision: "40"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e5699830a090f42feb92b24ec43fbae36634c4df
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="gs-buffer-security-check"></a>/GS (Sprawdzanie zabezpieczeń bufora)  
  
Wykrywa niektóre przepełnienia buforów, które zastępują adres zwrotny funkcji, adres aparatu obsługi wyjątków lub niektóre typy parametrów. Przepełnianie buforu to technika używana przez hakerów do wykorzystywania luk w kodzie, który nie wymusza ograniczeń rozmiaru buforu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/GS[-]  
```  
  
## <a name="remarks"></a>Uwagi  
  
**/ GS** jest domyślnie włączone. Jeśli aplikacja ma nie zagrożenie bezpieczeństwa, użyj **/GS-**. Aby uzyskać więcej informacji na temat **/GS**, zobacz [kompilatora zabezpieczeń sprawdza w głębokość](http://go.microsoft.com/fwlink/p/?linkid=7260). Aby uzyskać więcej informacji na temat pomijanie wykrywania przepełnienie buforu, zobacz [safebuffers](../../cpp/safebuffers.md).  
  
## <a name="security-checks"></a>Sprawdzanie zabezpieczeń  
  
W funkcjach, które kompilator uznaje za zagrożone problemem przepełnienia buforu, przydziela miejsce w stosie przed adresem zwrotnym. Przy wejściu do funkcji jest załadowana ilość miejsca przydzielonego *plik cookie zabezpieczeń* raz obliczonych na załadowanie modułu. Podczas zamykania funkcji oraz podczas usuwania ramek ze stosu (unwinding) w 64-bitowych systemach operacyjnych następuje wywołanie funkcji pomocnika, która sprawdza, czy wartość pliku cookie jest wciąż taka sama. Inna wartość wskazuje, że mogło dojść do zastąpienia stosu. Wykrycie innej wartości powoduje przerwanie procesu.  
  
## <a name="gs-buffers"></a>Bufory GS  
  
Sprawdzanie zabezpieczeń przepełnienie buforu jest wykonywana na *buforu GS*. Buforem GS może być jeden z następujących obiektów:  
  
-   Tablica, która jest większa niż 4 bajty, ma więcej niż dwa elementy oraz zawiera element typu innego niż wskaźnik.  
  
-   Struktura danych, która ma więcej niż 8 bajtów i nie zawiera żadnych wskaźników.  
  
-   Bufor przydzielony przy użyciu [_alloca](../../c-runtime-library/reference/alloca.md) funkcji.  
  
-   Dowolna klasa lub struktura zawierająca bufor GS.  
  
Na przykład poniższe instrukcje deklarują bufory GS.  
  
```cpp  
char buffer[20];  
int buffer[20];  
struct { int a; int b; int c; int d; } myStruct;  
struct { int a; char buf[20]; };  
```  
  
Natomiast następujące instrukcje nie deklarują buforów GS. Dwie pierwsze deklaracje zawierają elementy będące wskaźnikami. Instrukcje trzecia i czwarta deklarują tablice, które są za małe. Piąta instrukcja deklaruje strukturę, której rozmiar na platformie x86 jest nie większy niż 8 bajtów.  
  
```cpp  
char *pBuf[20];  
void *pv[20];  
char buf[4];  
int buf[2];  
struct { int a; int b; };  
```  
  
## <a name="initialize-the-security-cookie"></a>Inicjowanie pliku cookie zabezpieczeń  
  
**/GS** — opcja kompilatora wymaga zainicjowanej plik cookie zabezpieczeń przed uruchomieniem dowolnej funkcji, która używa pliku cookie. Plik cookie zabezpieczeń musi być zainicjowany natychmiast na zapis do pliku EXE lub DLL. Odbywa się to automatycznie Jeśli użyjesz domyślnych punktów wejścia VCRuntime: mainCRTStartup, wmainCRTStartup, WinMainCRTStartup, wWinMainCRTStartup, lub _DllMainCRTStartup. Użycie punktu wejścia alternatywne, należy ręcznie zainicjować plik cookie zabezpieczeń przez wywołanie metody [__security_init_cookie —](../../c-runtime-library/reference/security-init-cookie.md).  
  
## <a name="what-is-protected"></a>Co obejmuje ochrona  
  
**/GS** — opcja kompilatora chroni następujące elementy:  
  
-   Adres zwrotny wywołania funkcji.  
  
-   Adres aparatu obsługi wyjątków funkcji.  
  
-   Zagrożone parametry funkcji.  
  
Na wszystkich platformach **/GS** podejmuje próbę wykrycia przepełnienia buforu na adres zwrotny. Przepełnienia buforów łatwiej wykonać na platformach takich jak x86 i x64, ponieważ używają one konwencji wywoływania, które przechowują adresy zwrotne wywołań funkcji w stosach.  
  
Jeśli na platformie x86 funkcja używa aparatu obsługi wyjątków, kompilator wprowadza plik cookie zabezpieczeń chroniący adres tego aparatu. Plik cookie jest sprawdzany w trakcie usuwania ramek ze stosu.  
  
**/ GS** chroni *narażone parametry* przekazywane do funkcji. Do takich parametrów zalicza się wskaźniki, odwołania do składni języka C++, struktury języka C (typu C++ POD) zawierające wskaźniki oraz bufory GS.  
  
Parametr zagrożony jest przydzielany przed plikiem cookie i lokalnymi zmiennymi. Przepełnienie buforu może spowodować zastąpienie tych parametrów. Wtedy kod w funkcji wykorzystującej te parametry może doprowadzić do ataku, zanim funkcja zwróci wartość i zostanie wykonane sprawdzanie zabezpieczeń. Aby ograniczyć to zagrożenie, kompilator tworzy kopię zagrożonych parametrów w trakcie prologu funkcji i umieszcza je w obszarze pamięci masowej wykorzystywanym przez bufory.  
  
Kompilator nie tworzy kopii zagrożonych parametrów w następujących sytuacjach:  
  
-   Funkcje, które nie zawierają buforu GS.  
  
-   Optymalizacje ([/O opcje](../../build/reference/o-options-optimize-code.md)) nie są włączone.  
  
-   Funkcje o zmiennej liczbie argumentów (...).  
  
-   Funkcje, które są oznaczone ikoną z [naked](../../cpp/naked-cpp.md).  
  
-   Funkcje, które w pierwszej instrukcji zawierają wbudowany kod zestawu.  
  
-   Parametr jest wykorzystywany tylko na sposoby stanowiące mniejsze zagrożenie w razie przepełnienia buforu.  
  
## <a name="what-is-not-protected"></a>Czego nie obejmuje ochrona  
  
**/GS** — opcja kompilatora nie chroni przed takimi atakami, wszystkie przepełnienie buforu. Jeśli na przykład istnieje bufor oraz tabela wirtualna w obiekcie, przepełnienie buforu może spowodować uszkodzenie tabeli.  
  
Nawet jeśli używasz **/GS**, zawsze próbować bezpieczny kod, który ma nie przepełnienia buforu zapisu.  
  
### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**.  
  
     Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W **strony właściwości** okno dialogowe, kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **generowania kodu** strony właściwości.  
  
4.  Modyfikowanie **sprawdzanie zabezpieczeń bufora** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>.  
  
## <a name="example"></a>Przykład  
  
W tym przykładzie nastąpi przepełnienie buforu. Spowoduje to błąd aplikacji podczas wykonywania.  
  
```C  
// compile with: /c /W1  
#include <cstring>  
#include <stdlib.h>  
#pragma warning(disable : 4996)   // for strcpy use  
  
// Vulnerable function  
void vulnerable(const char *str) {  
   char buffer[10];  
   strcpy(buffer, str); // overrun buffer !!!  
  
   // use a secure CRT function to help prevent buffer overruns  
   // truncate string to fit a 10 byte buffer  
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);  
}  
  
int main() {  
   // declare buffer that is bigger than expected  
   char large_buffer[] = "This string is longer than 10 characters!!";  
   vulnerable(large_buffer);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
  
[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)