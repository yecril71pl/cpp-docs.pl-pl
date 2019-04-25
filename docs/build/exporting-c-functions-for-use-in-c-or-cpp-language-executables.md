---
title: Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub C++
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273576"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub C++

W przypadku funkcji w bibliotece DLL napisane w języku C, który chcesz uzyskać dostęp z języka C lub C++ modułu języka, należy użyć **__cplusplus** makro preprocesora Aby określić język, który jest kompilowany, a następnie je zadeklarować funkcje z powiązaniem C, jeśli są używane z C++ modułu języka. Jeśli korzystasz z tej techniki i udostępniają pliki nagłówka dla biblioteki DLL, te funkcje można używane przez C i C++ użytkowników bez zmian.

Poniższy kod przedstawia plik nagłówka, które mogą być używane przez aplikacje klienckie C i C++:

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

Jeśli musisz utworzyć link funkcji języka C do Twojego pliku wykonywalnego C++ oraz pliki nagłówkowe deklaracji funkcji nie użyto powyższej metody, w pliku źródłowego języka C++, wykonaj następujące polecenie, aby uniemożliwić kompilatorowi dekoracji nazwy funkcji C:

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików .def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Określić, której metody eksportowania użyjesz](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Zainicjuj bibliotekę DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Nazwy ozdobione](reference/decorated-names.md)

- [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Zobacz także

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
