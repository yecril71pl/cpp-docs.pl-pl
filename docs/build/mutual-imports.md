---
title: Importy wzajemne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bfd31cd4e5776555137daf002c076e14d4031f89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mutual-imports"></a>Importy wzajemne
Eksportowanie lub importowanie do innego pliku wykonywalnego przedstawia komplikacji, gdy Importy wzajemne (lub cykliczne). Na przykład dwa pliki dll importować symbole od siebie, podobnie jak funkcje wzajemnie rekursywne.  
  
 Problem z Ręczne importowanie plików wykonywalnych (zazwyczaj dll) jest, że nie mogą być tworzone bez tworzenia innych pierwszy. Każdy proces kompilacji wymaga jako dane wejściowe, biblioteki importu utworzone przez proces kompilacji.  
  
 Rozwiązaniem jest użycie narzędzia LIB z opcją/DEF, tworzy biblioteki importowanej bez tworzenia pliku wykonywalnego. Narzędzie to można utworzyć biblioteki importu należy, niezależnie od tego, jak wiele bibliotek DLL są zaangażowane lub stopnia złożoności są zależności.  
  
 Ogólne rozwiązanie do obsługi Importy wzajemne jest:  
  
1.  Z kolei zająć każdą bibliotekę DLL. (Dowolnej kolejności jest to możliwe, mimo że niektóre zlecenia są bardziej optymalne.) Jeśli wszystkie biblioteki importu wymagane istnieją i są aktualne, uruchom łącze, aby utworzyć plik wykonywalny (DLL). Daje to biblioteki importu. W przeciwnym wypadku Przeprowadź LIB do tworzenia biblioteki importu.  
  
     Uruchamianie LIB z opcją/DEF spowoduje utworzenie dodatkowego pliku z. EXP rozszerzenia. . Plik EXP należy później użyć do utworzenia pliku wykonywalnego.  
  
2.  Przy użyciu łącza lub LIB wszystkie biblioteki importu kompilacji, przejdź wstecz i uruchom łącze do kompilacji pliki wykonywalne, które nie zostały zbudowane w poprzednim kroku. Należy pamiętać, że odpowiedniego pliku .exp należy określić w wierszu łącza.  
  
     Po uruchomieniu narzędzia LIB wcześniej do utworzenia biblioteki importowanej dla DLL1, LIB czy utworzony plik DLL1.exp również. Podczas kompilowania DLL1.dlll, należy użyć DLL1.exp jako dane wejściowe, łącza.  
  
 Na poniższej ilustracji przedstawiono rozwiązanie dla dwóch wzajemnie importowania biblioteki dll, DLL1 i DLL2. Krok 1 jest uruchamianie LIB, z ustawioną opcją/DEF na DLL1. Krok 1 tworzy DLL1.lib, biblioteki importowanej oraz DLL1.exp. W kroku 2 biblioteki importu jest używany do tworzenia DLL2, który z kolei biblioteki importowanej dla symboli w DLL2. Krok 3 tworzy DLL1, przy użyciu DLL1.exp i DLL2.lib jako dane wejściowe. Należy pamiętać, że pliku .exp DLL2 nie jest konieczne, ponieważ LIB nie został użyty do tworzenia biblioteki importu DLL2 firmy.  
  
 ![Aby połączyć dwie biblioteki DLL przy użyciu Importy wzajemne](../build/media/vc37yj1.gif "vc37YJ1")  
Łączenie dwóch bibliotek DLL z Importy wzajemne  
  
## <a name="limitations-of-afxext"></a>Ograniczenia _AFXEXT  
 Można użyć `_AFXEXT` symbol preprocesora tak długo, jak nie ma wiele warstw biblioteki DLL rozszerzeń MFC z biblioteki DLL rozszerzenia MFC. Jeśli masz rozszerzenia MFC dll, które wywołania lub pochodzić od klasy własne rozszerzenia MFC dll, które następnie pochodzi od klasy MFC, należy użyć symbol preprocesora, aby uniknąć niejednoznaczności.  
  
 Problem jest tym w Win32, musisz jawnie zadeklarować wszystkie dane jako **__declspec(dllexport)** w celu wyeksportowania z biblioteki DLL, i **__declspec(dllimport)** w celu zaimportowania z biblioteki DLL. Podczas definiowania `_AFXEXT`, nagłówki MFC, upewnij się, że **afx_ext_class —** jest poprawnie zdefiniowany.  
  
 Jeśli masz wiele warstw, jeden symbol takich jak **afx_ext_class —** nie wystarcza, ponieważ bibliotekę DLL rozszerzenia MFC mogą być eksportowanie nowe klasy, a także importowanie innych klas z inną bibliotekę DLL rozszerzenia MFC. Aby rozwiązać ten problem, Użyj specjalnych symbol preprocesora, który wskazuje, czy tworzysz DLL porównaniu z użyciem biblioteki DLL. Załóżmy na przykład dwie biblioteki DLL rozszerzenia MFC, A.dll i B.dll. Niektóre klasy A.h i B.h, każdy z nich wyeksportować odpowiednio. B.dll korzysta z klas z A.dll. Pliki nagłówkowe będzie wyglądać mniej więcej tak:  
  
```  
/* A.H */  
#ifdef A_IMPL  
   #define CLASS_DECL_A   __declspec(dllexport)  
#else  
   #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
  
// B.H  
#ifdef B_IMPL  
   #define CLASS_DECL_B   __declspec(dllexport)  
#else  
   #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition ... };  
...  
```  
  
 Po utworzeniu A.dll został skompilowany za `/D A_IMPL` i po utworzeniu B.dll został skompilowany za `/D B_IMPL`. Przy użyciu osobnych symbole dla każdej biblioteki DLL `CExampleB` są eksportowane i `CExampleA` jest importowany podczas kompilowania B.dll. `CExampleA`wyeksportowaniu podczas kompilowania A.dll i zaimportowane, gdy jest używana przez B.dll (lub innego klienta).  
  
 Tworzenie warstw tego typu nie można wykonać przy użyciu wbudowanych **afx_ext_class —** i `_AFXEXT` symboli preprocesora. Techniki opisane powyżej rozwiązuje ten problem w sposób nie w przeciwieństwie do mechanizmu MFC sam używa podczas kompilowania jego technologii Active, bazy danych i bibliotek DLL rozszerzeń MFC sieci.  
  
## <a name="not-exporting-the-entire-class"></a>Nie eksportowania całej klasy  
 Gdy nie są eksportowane całej klasy, należy zapewnić poprawnie wyeksportowane elementy potrzebne dane utworzone przez makr MFC. Można to zrobić przez ponowne definiowanie `AFX_DATA` makra określonej klasy. Należy to zrobić z dowolnym momencie całej klasy nie są eksportowane.  
  
 Na przykład:  
  
```  
/* A.H */  
#ifdef A_IMPL  
   #define CLASS_DECL_A  _declspec(dllexport)  
#else  
   #define CLASS_DECL_A  _declspec(dllimport)  
#endif  
  
#undef  AFX_DATA  
#define AFX_DATA CLASS_DECL_A  
  
class CExampleA : public CObject  
{  
   DECLARE_DYNAMIC()  
   CLASS_DECL_A int SomeFunction();  
   //... class definition ...  
};  
  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu. Pliki DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Narzędzie LIB wraz z opcją/DEF](../build/reference/lib-reference.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie i eksportowanie](../build/importing-and-exporting.md)