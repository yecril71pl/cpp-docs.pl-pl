---
title: Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: a694b77e3730ab82ec1698076cc66729ff115cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195237"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C

Jeśli masz funkcji w bibliotece DLL napisanego w języku C++, że chcesz uzyskać dostęp z modułu języka C, należy zadeklarować tych funkcji z powiązaniem C zamiast powiązania C++. O ile nie określono inaczej, kompilator języka C++ używa C++ bezpieczny nazewnictwa (nazwij dekorację) i C++, Konwencje wywoływania, które mogą być trudne do wywoływania z C.

Aby określić powiązanie C, należy określić `extern "C"` dla swojej deklaracji funkcji. Na przykład:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików .def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C do użycia w plikach wykonywalnych języka C lub języka C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Określić, której metody eksportowania użyjesz](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Zainicjuj bibliotekę DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Nazwy ozdobione](reference/decorated-names.md)

- [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Zobacz także

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
