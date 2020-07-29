---
title: Importy wzajemne
ms.date: 11/04/2016
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
ms.openlocfilehash: 771ce7506359178c1b8346598e93c30a20329fe8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229795"
---
# <a name="mutual-imports"></a>Importy wzajemne

Eksportowanie lub importowanie do innego pliku wykonywalnego przedstawia komplikacje, gdy Importy są wzajemnie (lub cykliczne). Na przykład dwie biblioteki DLL importują symbole ze sobą, podobnie jak funkcje wzajemnie cykliczne.

Problem związany ze wzajemnym importowaniem plików wykonywalnych (zwykle dll) jest taki, że nie można kompilować ani utworzyć drugiego. Każdy proces kompilacji wymaga, jako dane wejściowe, biblioteki importu utworzonej przez inny proces kompilacji.

Rozwiązaniem jest użycie narzędzia LIB z opcją/DEF, która tworzy bibliotekę importu bez kompilowania pliku wykonywalnego. Za pomocą tego narzędzia można kompilować wszystkie potrzebne biblioteki importu, niezależnie od tego, ile bibliotek DLL jest używanych, lub jak skomplikowane są zależności.

Ogólne rozwiązanie do obsługi wzajemnych importów to:

1. Przełącz każdą bibliotekę DLL z kolei. (Dowolna kolejność jest wykonalna, chociaż niektóre zamówienia są bardziej optymalne). Jeśli wszystkie wymagane biblioteki importowe istnieją i są aktualne, uruchom LINK, aby skompilować plik wykonywalny (DLL). Spowoduje to utworzenie biblioteki importu. W przeciwnym razie uruchom LIB, aby utworzyć bibliotekę importu.

   Uruchomienie LIB z opcją/DEF powoduje utworzenie dodatkowego pliku z rozszerzeniem. Rozszerzenie EXP. Polu. Plik EXP musi być później używany do kompilowania pliku wykonywalnego.

1. Po użyciu LINKu lub LIB do skompilowania wszystkich bibliotek importu, wróć i uruchom LINK, aby skompilować wszystkie pliki wykonywalne, które nie zostały skompilowane w poprzednim kroku. Należy pamiętać, że odpowiedni plik EXP musi być określony w wierszu łącza.

   Jeśli narzędzie LIB zostało wcześniej uruchomione w celu utworzenia biblioteki Imports dla DLL1, LIB również wyprodukował plik DLL1. EXP. Musisz użyć DLL1. EXP jako danych wejściowych do KONSOLIDACJi podczas kompilowania DLL1.dlll.

Na poniższej ilustracji przedstawiono rozwiązanie dla dwóch wzajemnie importowanych bibliotek DLL, DLL1 i DLL2. Krok 1. Aby uruchomić LIB, z ustawioną opcją/DEF na DLL1. Krok 1 powoduje utworzenie DLL1. lib, biblioteki Import i DLL1. EXP. W kroku 2 Biblioteka importowania jest używana do kompilowania DLL2, co z kolei powoduje utworzenie biblioteki Import dla symboli DLL2's. Krok 3 kompiluje DLL1, używając DLL1. exp i DLL2. lib jako dane wejściowe. Należy zauważyć, że plik. EXP dla DLL2 nie jest potrzebny, ponieważ LIB nie został użyty do skompilowania biblioteki importu DLL2's.

![Łączenie dwóch bibliotek DLL przy użyciu wzajemnych importów](media/vc37yj1.gif "Łączenie dwóch bibliotek DLL przy użyciu wzajemnych importów")<br/>
Łączenie dwóch bibliotek DLL z wzajemnymi importami

## <a name="limitations-of-_afxext"></a>Ograniczenia _AFXEXT

Możesz użyć `_AFXEXT` symbolu preprocesora dla bibliotek DLL rozszerzenia MFC, o ile nie masz wielu warstw bibliotek DLL rozszerzeń MFC. Jeśli masz biblioteki DLL rozszerzenia MFC, które wywołują lub pochodzą z klas we własnych bibliotekach DLL rozszerzenia MFC, które następnie pochodzą od klas MFC, należy użyć własnego symbolu preprocesora, aby uniknąć niejednoznaczności.

Problem polega na tym, że w systemie Win32 należy jawnie zadeklarować wszelkie dane tak, jakby zostały **`__declspec(dllexport)`** wyeksportowane z biblioteki DLL, i **`__declspec(dllimport)`** Jeśli ma zostać zaimportowany z biblioteki DLL. Podczas definiowania `_AFXEXT` , nagłówki MFC upewnij się, że **AFX_EXT_CLASS** jest prawidłowo zdefiniowany.

Jeśli masz wiele warstw, jeden symbol taki jak **AFX_EXT_CLASS** nie jest wystarczający, ponieważ biblioteka DLL rozszerzenia MFC może eksportować nowe klasy, a także importować inne klasy z innej biblioteki DLL rozszerzenia MFC. Aby rozwiązać ten problem, należy użyć specjalnego symbolu preprocesora, który wskazuje, że tworzysz bibliotekę DLL zamiast korzystać z biblioteki DLL. Załóżmy na przykład, że istnieją dwie biblioteki DLL rozszerzenia MFC, A.dll i B.dll. Każdy z nich eksportuje kilka klas odpowiednio do. h i B. h. B.dll używa klas z A.dll. Pliki nagłówkowe będą wyglądać następująco:

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

Po skompilowaniu A.dll jest on zbudowany z `/D A_IMPL` i po skompilowaniu B.dll jest on zbudowany przy użyciu `/D B_IMPL` . Przy użyciu oddzielnych symboli dla każdej biblioteki DLL `CExampleB` jest eksportowany i `CExampleA` importowany podczas kompilowania B.dll. `CExampleA`jest eksportowany podczas kompilowania A.dll i importowania, gdy jest używany przez B.dll (lub innego klienta).

Tego typu warstw nie można wykonać w przypadku używania wbudowanych **AFX_EXT_CLASS** i `_AFXEXT` symboli preprocesora. Opisana powyżej technika pozwala rozwiązać ten problem w sposób, który nie jest w przeciwieństwie do mechanizmu MFC, który używa w przypadku kompilowania aktywnych technologii, bazy danych i bibliotek DLL rozszerzeń MFC.

## <a name="not-exporting-the-entire-class"></a>Nie eksportuje całej klasy

Gdy nie eksportujesz całej klasy, musisz upewnić się, że niezbędne elementy danych utworzone przez makra MFC są poprawnie wyeksportowane. Można to zrobić przez ponowne zdefiniowanie `AFX_DATA` do makra konkretnej klasy. Należy to zrobić za każdym razem, gdy nie eksportujesz całej klasy.

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

- [Eksportuj z biblioteki DLL](exporting-from-a-dll.md)

- [Eksportowanie z biblioteki DLL przy użyciu programu. Pliki DEF](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Wybieranie metody eksportowania do użycia](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Narzędzie LIB i opcja/DEF](reference/lib-reference.md)

## <a name="see-also"></a>Zobacz także

[Importowanie i eksportowanie](importing-and-exporting.md)
