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
ms.openlocfilehash: e4ac48dc013874c240411f78a733d32e116df25d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223970"
---
# <a name="importing-using-def-files"></a>Importowanie przy użyciu plików DEF

Jeśli zdecydujesz się używać **`__declspec(dllimport)`** razem z plikiem. def, należy zmienić plik. def, aby użyć danych zamiast stałej, aby zmniejszyć prawdopodobieństwo, że nieprawidłowe kodowanie spowoduje wystąpienie problemu:

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

Używanie **`__declspec(dllimport)`** i stałe wyświetla zarówno `imp` wersję, jak i niedekoracyjną nazwę w bibliotece importu dll. lib, która została utworzona w celu zezwalania na jawne łączenie. Użycie **`__declspec(dllimport)`** i dane wyświetlają tylko `imp` wersję nazwy.

Jeśli używasz stałej, można uzyskać dostęp do następujących konstrukcji kodu `ulDataInDll` :

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-oraz

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Jeśli jednak używasz danych w pliku. def, tylko kod skompilowany przy użyciu następującej definicji może uzyskać dostęp do zmiennej `ulDataInDll` :

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Użycie stałej jest bardziej ryzykowne, ponieważ jeśli zapomnisz użyć dodatkowego poziomu pośredniego, możesz uzyskać dostęp do wskaźnika tabeli adresów importu do zmiennej — a nie do samej zmiennej. Ten typ problemu może często przejawiać się jako naruszenie zasad dostępu, ponieważ tabela adresów importu jest obecnie wykonywana tylko do odczytu przez kompilator i konsolidator.

Bieżący konsolidator MSVC wyświetla ostrzeżenie, jeśli w pliku. def zostanie wyświetlona stała dla tego przypadku. Jedyną przyczyną użycia stałej jest to, że nie można ponownie skompilować pliku obiektu, w którym plik nagłówka nie został wystawiony **`__declspec(dllimport)`** na prototypie.

## <a name="see-also"></a>Zobacz także

[Importowanie do aplikacji](importing-into-an-application.md)
