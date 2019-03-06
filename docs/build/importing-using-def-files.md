---
title: Importowanie przy użyciu plików DEF
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: f6e553a85e6c17a3ea914365ad29ad5136e50629
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424784"
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

## <a name="see-also"></a>Zobacz także

[Importowanie do aplikacji](../build/importing-into-an-application.md)
