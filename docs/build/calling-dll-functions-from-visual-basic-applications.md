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
ms.openlocfilehash: 23b5692e28b9ea5b70c492e2564b8bf5385b1815
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221196"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Wywoływanie funkcji DLL z aplikacji języka Visual Basic

W przypadku aplikacji Visual Basic (lub aplikacji w innych językach, takich jak Pascal lub Pascal) wywoływanie funkcji w bibliotece DLL C/C++, funkcje muszą zostać wyeksportowane przy użyciu poprawnej konwencji wywoływania bez dekoracji nazw wykonanych przez kompilator.

`__stdcall`tworzy właściwą konwencję wywoływania dla funkcji (wywoływana funkcja czyści stos, a parametry są przesyłane od prawej do lewej), ale zdobi nazwę funkcji inaczej. Tak więc gdy **__declspec (dllexport)** jest używany w wyeksportowanej funkcji w bibliotece DLL, nazwa dekoracyjna zostanie wyeksportowana.

Dekoracja `__stdcall` nazwy prefiksu nazwy symbolu z podkreśleniem ( **\_** ) i dołącza symbol ze znakiem znaku (**\@**), po którym następuje liczba bajtów na liście argumentów (wymagana przestrzeń stosu). W związku z tym funkcja jest zadeklarowana jako:

```C
int __stdcall func (int a, double b)
```

ma charakter `_func@12` w danych wyjściowych.

Konwencja wywoływania C (`__cdecl`) zdobi nazwę jako. `_func`

Aby uzyskać nazwę dekoracyjną, użyj [/map](reference/map-generate-mapfile.md). Użycie **__declspec (dllexport)** wykonuje następujące czynności:

- Jeśli funkcja zostanie wyeksportowana przy użyciu konwencji wywoływania C`__cdecl`(), nakreśli wiodący znak **\_** podkreślenia (), gdy nazwa zostanie wyeksportowana.

- Jeśli eksportowana funkcja nie używa konwencji wywoływania C (na przykład `__stdcall`), eksportuje nazwę dekoracyjną.

Ponieważ nie ma sposobu, aby przesłonić miejsce, w którym występuje oczyszczanie `__stdcall`stosu, należy użyć. Aby undecorate nazwy z `__stdcall`, należy je określić przy użyciu aliasów w sekcji eksporty pliku. def. Jest to pokazane w następujący sposób dla następującej deklaracji funkcji:

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

W przypadku bibliotek DLL, które mają być wywoływane przez programy w Visual Basic, technika aliasu pokazana w tym temacie jest wymagana w pliku. def. Jeśli alias jest wykonywany w programie Visual Basic, użycie aliasu w pliku. def nie jest konieczne. Można to zrobić w programie Visual Basic, dodając klauzulę aliasu do instrukcji [DECLARE](/dotnet/visual-basic/language-reference/statements/declare-statement) .

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)

- [Eksportowanie z biblioteki DLL przy użyciu programu. Pliki DEF](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Określanie, której metody eksportowania użyć](determining-which-exporting-method-to-use.md)

- [Nazwy dekoracyjne](reference/decorated-names.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
