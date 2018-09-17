---
title: Importowanie przy użyciu plików DEF | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e1562e14b20e4e1dd96764414978889d6205179
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710544"
---
# <a name="importing-using-def-files"></a>Importowanie przy użyciu plików DEF

Jeśli zdecydujesz się używać **__declspec(dllimport)** wraz z plikiem .def, należy zmienić plik .def, aby użyć danych zamiast STAŁA Aby zmniejszyć prawdopodobieństwo, że nieprawidłowe kodowanie spowoduje, że problem:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

W poniższej tabeli przedstawiono dlaczego.

|Słowo kluczowe|Emituje w bibliotece importu|Eksporty|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

Za pomocą **__declspec(dllimport)** i STAŁA wyświetla zarówno `imp` wersji i nieozdobioną nazwę zawartej w .lib DLL Importuj biblioteki, który jest tworzony umożliwia jawne tworzenie łączy. Za pomocą **__declspec(dllimport)** listy danych i po prostu z `imp` wersja nazwy.

Jeśli używasz STAŁĄ, jedną z następujących konstrukcji kodu może służyć do dostępu `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-lub —

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Jednak jeśli używasz danych w pliku .def, tylko kod skompilowany przy użyciu następującej definicji mają dostęp do zmiennej `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Przy użyciu stałej jest bardziej ryzykowne, ponieważ Jeśli zapomnisz dodatkowy poziom pośredni, użytkownik może potencjalnie uzyskać dostęp do tabeli adresów importowania wskaźnik do zmiennej — nie zmiennej. Tego rodzaju problem można często manifestu jako naruszenie zasad dostępu, ponieważ tabeli adresów importowania jest obecnie tylko do odczytu przez kompilatora i konsolidatora.

Bieżący konsolidatora Visual C++ generuje ostrzeżenie, jeśli STAŁĄ w pliku .def konta dla tej sprawy. Tylko rzeczywistego powód, aby używało — STAŁA jest, jeśli nie można ponownie skompilować niektóre pliku obiektu, gdy plik nagłówkowy nie listy **__declspec(dllimport)** na prototypu.

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](../build/importing-into-an-application.md)
