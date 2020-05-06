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
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273420"
---
# <a name="importing-using-def-files"></a>Importowanie przy użyciu plików DEF

Jeśli zdecydujesz się używać **__declspec (dllimport)** wraz z plikiem. def, należy zmienić plik. def, aby użyć danych zamiast stałej, aby zmniejszyć prawdopodobieństwo, że niewłaściwe kodowanie spowoduje wystąpienie problemu:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

W poniższej tabeli przedstawiono przyczynę.

|Słowo kluczowe|Emituje w bibliotece import|Eksportowanie|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

Używanie **__declspec (dllimport)** i stałych wyświetla zarówno `imp` wersję, jak i niedekoracyjną nazwę w bibliotece importu dll. lib, która została utworzona w celu zezwalania na jawne łączenie. Używanie **__declspec (dllimport)** i danych wyświetla tylko `imp` wersję nazwy.

Jeśli używasz stałej, można uzyskać dostęp `ulDataInDll`do następujących konstrukcji kodu:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-oraz

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Jeśli jednak używasz danych w pliku. def, tylko kod skompilowany przy użyciu następującej definicji może uzyskać dostęp do zmiennej `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Użycie stałej jest bardziej ryzykowne, ponieważ jeśli zapomnisz użyć dodatkowego poziomu pośredniego, możesz uzyskać dostęp do wskaźnika tabeli adresów importu do zmiennej — a nie do samej zmiennej. Ten typ problemu może często przejawiać się jako naruszenie zasad dostępu, ponieważ tabela adresów importu jest obecnie wykonywana tylko do odczytu przez kompilator i konsolidator.

Bieżący konsolidator MSVC wyświetla ostrzeżenie, jeśli w pliku. def zostanie wyświetlona stała dla tego przypadku. Jedyną przyczyną użycia stałej jest to, że nie można ponownie skompilować niektórych plików obiektów, gdzie plik nagłówkowy nie zawiera listy **__declspec (dllimport)** w prototypie.

## <a name="see-also"></a>Zobacz też

[Importowanie do aplikacji](importing-into-an-application.md)
