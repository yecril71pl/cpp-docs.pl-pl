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
ms.openlocfilehash: 8d792dac45d69a0857bda551d1f3c03fc3d03d1c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229886"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Wywoływanie funkcji DLL z aplikacji języka Visual Basic

W przypadku aplikacji Visual Basic (lub aplikacji w innych językach, takich jak Pascal lub Pascal) wywoływanie funkcji w bibliotece DLL C/C++, funkcje muszą zostać wyeksportowane przy użyciu poprawnej konwencji wywoływania bez dekoracji nazw wykonanych przez kompilator.

**`__stdcall`** tworzy właściwą konwencję wywoływania dla funkcji (wywoływana funkcja czyści stos, a parametry są przesyłane od prawej do lewej), ale zdobi nazwę funkcji inaczej. Dlatego, gdy **`__declspec(dllexport)`** jest używany w wyeksportowanej funkcji w bibliotece DLL, nazwa dekoracyjna jest eksportowana.

**`__stdcall`** Dekoracja nazwy prefiksu nazwy symbolu z podkreśleniem ( **\_** ) i dołącza symbol ze **\@** znakiem znaku (), po którym następuje liczba bajtów na liście argumentów (wymagana przestrzeń stosu). W związku z tym funkcja jest zadeklarowana jako:

```C
int __stdcall func (int a, double b)
```

ma charakter `_func@12` w danych wyjściowych.

Konwencja wywoływania C ( **`__cdecl`** ) zdobi nazwę jako `_func` .

Aby uzyskać nazwę dekoracyjną, użyj [/map](reference/map-generate-mapfile.md). W tym celu należy wykonać **`__declspec(dllexport)`** następujące czynności:

- Jeśli funkcja zostanie wyeksportowana przy użyciu konwencji wywoływania C ( **`__cdecl`** ), nakreśli wiodący znak podkreślenia ( **\_** ), gdy nazwa zostanie wyeksportowana.

- Jeśli eksportowana funkcja nie używa konwencji wywoływania C (na przykład **`__stdcall`** ), eksportuje nazwę dekoracyjną.

Ponieważ nie ma sposobu, aby przesłonić miejsce, w którym występuje oczyszczanie stosu, należy użyć **`__stdcall`** . Aby undecorate nazwy z **`__stdcall`** , należy je określić przy użyciu aliasów w sekcji eksporty pliku. def. Jest to pokazane w następujący sposób dla następującej deklaracji funkcji:

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

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Wybieranie metody eksportowania do użycia](determining-which-exporting-method-to-use.md)

- [Nazwy ozdobione](reference/decorated-names.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
