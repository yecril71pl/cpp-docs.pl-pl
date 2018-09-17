---
title: Importy wzajemne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7aee01e72fb8386b6aee7e6a505424b4138f45d7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704850"
---
# <a name="mutual-imports"></a>Importy wzajemne

Eksportowanie lub importowanie do innego pliku wykonywalnego przedstawia informacje o kompilacji w przypadku Importy wzajemne (lub cykliczne). Na przykład dwa pliki dll zaimportować symbole od siebie nawzajem, podobnie jak funkcje wzajemnie rekursywne.

Problem dotyczący Ręczne importowanie plików wykonywalnych (zazwyczaj dll) jest, nie mogą być wbudowane w bez potrzeby tworzenia innych pierwszy. Każdy proces kompilacji wymaga jako dane wejściowe, biblioteki importowanej generowany przez proces kompilacji.

Rozwiązanie jest użycie narzędzia LIB z opcją/DEF, który tworzy bibliotekę importu bez konieczności tworzenia pliku wykonywalnego. Narzędzie to można tworzyć wszystkie biblioteki importu, potrzebujesz, niezależnie od tego, ile biblioteki DLL są zaangażowane lub stopnia złożoności są zależności.

Ogólne rozwiązanie do obsługi Importy wzajemne jest:

1. Skorzystaj z kolei każdej biblioteki DLL. (Wszystkie zamówienia jest to możliwe, chociaż niektóre zamówienia są bardziej optymalne.) Jeśli wszystkie biblioteki importu potrzebne istnieje, a to wartości bieżące, LINK do tworzenia pliku wykonywalnego (DLL) do uruchamiania. Tworzy to bibliotekę importu. W przeciwnym razie uruchom LIB, aby wygenerować bibliotekę importu.

   Uruchamianie LIB z opcją/DEF tworzy dodatkowy plik za pomocą. EXP rozszerzenie. . Plik EXP musi być później używany do tworzenia pliku wykonywalnego.

1. Po za pomocą łącza lub LIB Kompiluj wszystko z bibliotekami importowanymi, przejdź wstecz i uruchom LINK, aby tworzyć pliki wykonywalne, które nie zostały utworzone w poprzednim kroku. Należy pamiętać, że odpowiedni plik .exp musi zostać określony w wierszu łącza.

   Po uruchomieniu narzędzia LIB wcześniej, aby wygenerować bibliotekę importu dla DLL1, LIB będzie generowany plik DLL1.exp, jak również. Podczas tworzenia DLL1.dlll, należy użyć DLL1.exp jako dane wejściowe do łącza.

Poniższa ilustracja przedstawia rozwiązania dla dwóch wzajemnie się importowanie bibliotek DLL, DLL1 i DLL2. Krok 1 jest uruchamianie LIB, z ustawioną opcją/DEF na DLL1. Krok 1 tworzy DLL1.lib biblioteki importowanej oraz DLL1.exp. W kroku 2 Biblioteka importowana jest używany do tworzenia DLL2, który z kolei tworzy bibliotekę importu dla symboli DLL2 firmy. Krok 3 tworzy DLL1, przy użyciu DLL1.exp i DLL2.lib jako dane wejściowe. Należy pamiętać, że plik .exp dla DLL2 nie jest konieczne, ponieważ LIB nie był używany do tworzenia biblioteki importowanej DLL2 firmy.

![Aby połączyć dwa pliki dll za pomocą Importy wzajemne](../build/media/vc37yj1.gif "połączyć dwa pliki dll za pomocą Importy wzajemne")<br/>
Łączenie dwóch bibliotek DLL z Importy wzajemne

## <a name="limitations-of-afxext"></a>Ograniczenia _afxext —

Możesz użyć `_AFXEXT` symbol preprocesora dla rozszerzenia MFC biblioteki DLL tak długo, ponieważ nie masz wiele warstw biblioteki DLL rozszerzeń MFC. Jeśli masz rozszerzenia MFC biblioteki dll, takich jak wywoływanie lub pochodzić od klasy własne rozszerzenia MFC biblioteki dll, które następnie pochodzić od klasy MFC, musi użyć symbol preprocesora Aby uniknąć niejednoznaczności.

Problem polega na tym w Win32, należy jawnie deklarować, że wszystkie dane jako **__declspec(dllexport)** jeśli mają zostać wyeksportowane z biblioteki DLL, a **__declspec(dllimport)** przypadku ma zostać zaimportowany z biblioteki DLL. Podczas definiowania `_AFXEXT`, nagłówki MFC, upewnij się, że **AFX_EXT_CLASS** jest poprawnie zdefiniowany.

Jeśli masz wiele warstw, jeden symbol taki jak **AFX_EXT_CLASS** nie wystarcza, ponieważ rozszerzenia MFC DLL może być eksportowanie nowych klas, a także importowanie innych klas z innej biblioteki DLL rozszerzenia MFC. Aby rozwiązać ten problem, należy użyć specjalnego symbol preprocesora, który wskazuje, czy tworzysz DLL w przeciwieństwie do użycia biblioteki DLL. Załóżmy, że dwie biblioteki DLL rozszerzeń MFC, A.dll i B.dll. Niektóre klasy w A.h i B.h, ich eksportowanie odpowiednio. B.dll korzysta z klas z A.dll. Pliki nagłówkowe będą wyglądać mniej więcej tak:

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

Podczas kompilowania A.dll bazuje na `/D A_IMPL` i podczas kompilowania B.dll bazuje na `/D B_IMPL`. Przy użyciu oddzielnych symbole dla każdej biblioteki DLL `CExampleB` są eksportowane i `CExampleA` jest importowany podczas tworzenia B.dll. `CExampleA` jest wyeksportowany podczas tworzenia A.dll i zaimportować, gdy jest używana przez B.dll (lub innego klienta).

Nie można wykonać tego rodzaju warstw, korzystając z wbudowanej **AFX_EXT_CLASS** i `_AFXEXT` symboli preprocesora. Opisaną technikę rozwiązuje ten problem, w sposób nie w przeciwieństwie do mechanizmu MFC sam używa podczas tworzenia jej technologii Active bazy danych i bibliotek DLL rozszerzeń MFC sieci.

## <a name="not-exporting-the-entire-class"></a>Eksportowanie nie całej klasy

Gdy nie są eksportowane całej klasy, należy poprawnie wyeksportowane elementów niezbędnych danych, utworzonych przez makr MFC. Można to zrobić poprzez zmianę definicji `AFX_DATA` makra określonej klasy. Należy to określić ilekroć całej klasy nie są eksportowane.

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

- [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)

- [Eksportowanie z biblioteki DLL za pomocą. Pliki DEF](../build/exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Określić, której metody eksportowania użyjesz](../build/determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Narzędzie LIB i opcja/DEF](../build/reference/lib-reference.md)

## <a name="see-also"></a>Zobacz też

[Importowanie i eksportowanie](../build/importing-and-exporting.md)