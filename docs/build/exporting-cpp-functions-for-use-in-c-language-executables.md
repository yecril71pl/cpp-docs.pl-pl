---
title: Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: 38b13c1fc9c57354ba8160f6dbe0df6546fe7b5f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506609"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C

Jeśli masz funkcje w bibliotece DLL zapisaną w języku C++, do której chcesz uzyskać dostęp z modułu języka C, należy zadeklarować te funkcje przy użyciu powiązania C zamiast powiązania C++. O ile nie określono inaczej, kompilator języka C++ używa nazw i konwencji wywoływania języka C++, które mogą być trudne do wywołania z dysku C.

Aby określić powiązanie C, określ `extern "C"` dla deklaracji funkcji. Na przykład:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików. def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji C do użycia w plikach wykonywalnych języka C lub C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Wybieranie metody eksportowania do użycia](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Nazwy ozdobione](reference/decorated-names.md)

- [Użycie zewnętrznie w celu określenia powiązania](../cpp/extern-cpp.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
