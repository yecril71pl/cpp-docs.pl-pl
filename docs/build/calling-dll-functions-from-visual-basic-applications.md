---
title: Wywoływanie funkcji DLL z aplikacji języka Visual Basic
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 1e4f1a538da2394c6cead6ea011faf126b022a3f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814972"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Wywoływanie funkcji DLL z aplikacji języka Visual Basic

Dla aplikacji Visual Basic (lub aplikacje w innych językach, takich jak FORTRAN czy Pascal) mogły wywołać funkcje w bibliotece DLL C/C++ funkcje muszą zostać wyeksportowane z przy użyciu poprawnej konwencji wywoływania, bez dekorowania nazw wykonywanego przez kompilator

`__stdcall` Tworzy poprawne konwencja wywołania funkcji (wywołana funkcja czyści stos i parametry są przekazywane od prawej do lewej), ale zdobi nazwy funkcji w inny sposób. Więc, gdy **__declspec(dllexport)** jest używany na eksportowanych funkcji w bibliotece DLL, nazwa uzupełniona jest eksportowana.

`__stdcall` Dekorowania nazw prefiksów nazwę symbolu ze znakiem podkreślenia ( **\_** ) i dołącza symbol ze znakiem (**\@**) znakiem następuje liczba Liczba bajtów na liście argumentów (wymagany obszar stosu). W rezultacie, funkcja, gdy zadeklarowana jako:

```C
int __stdcall func (int a, double b)
```

jest urządzony jako `_func@12` w danych wyjściowych.

Konwencja wywoływania C (`__cdecl`) rozszerza nazwę jako `_func`.

Aby uzyskać nazwę z atrybutami, użyj [/MAP](reference/map-generate-mapfile.md). Korzystanie z **__declspec(dllexport)** wykonuje następujące czynności:

- Jeśli funkcja jest eksportowana z Konwencją wywoływania C (`__cdecl`), usuwa wiodący znak podkreślenia ( **\_** ) kiedy nazwa jest eksportowana.

- Jeśli eksportowana funkcja nie korzysta z konwencji wywoływania C (na przykład `__stdcall`), eksportuje ona również nazwę uzupełnioną.

Ponieważ nie istnieje sposób do przesłonięcia, gdzie występuje Oczyszczanie stosu, należy użyć `__stdcall`. Aby zdjąć atrybuty z nazw `__stdcall`, musisz określić je używając aliasów w sekcji EXPORTS pliku .def. To jest pokazana w poniższej deklaracji funkcji:

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

W. Plik DEF:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

W przypadku biblioteki DLL były wywołane przez programy napisane w języku Visual Basic w pliku .def potrzeby technikę aliasów, przedstawione w tym temacie. Jeśli alias został wykonany w programie Visual Basic, użycie aliasów w pliku .def nie jest konieczne. Możesz w programie Visual Basic przez dodanie klauzuli aliasu do [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) instrukcji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)

- [Eksportowanie z biblioteki DLL za pomocą. Pliki DEF](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie funkcji C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Określić, której metody eksportowania użyjesz](determining-which-exporting-method-to-use.md)

- [Nazwy ozdobione](reference/decorated-names.md)

## <a name="see-also"></a>Zobacz także

[Biblioteki DLL w programie Visual C++](dlls-in-visual-cpp.md)
