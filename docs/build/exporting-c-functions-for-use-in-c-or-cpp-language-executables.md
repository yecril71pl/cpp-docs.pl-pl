---
title: Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C++ lub C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88d9b18620c2e648ab519a59745876569b66ec30
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708100"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub C++

W przypadku funkcji w bibliotece DLL w języku C, którego chcesz uzyskać dostęp z języka C lub modułu języka C++, należy użyć **__cplusplus** makro preprocesora Aby określić język, który jest kompilowany, a następnie je zadeklarować funkcji z powiązaniem C, jeśli są używane z modułu języka C++. Jeśli korzystasz z tej techniki i udostępniają pliki nagłówka dla biblioteki DLL, te funkcje można używane przez C i C++ użytkowników bez zmian.

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

- [Eksportowanie z biblioteki DLL za pomocą plików .def](../build/exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Określić, której metody eksportowania użyjesz](../build/determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Zainicjuj bibliotekę DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Nazwy ozdobione](../build/reference/decorated-names.md)

- [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)