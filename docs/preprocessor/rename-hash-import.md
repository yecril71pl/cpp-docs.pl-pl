---
title: Zmień nazwę atrybutu importu
ms.date: 08/29/2019
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: ef1f64e0c268f850899efe499f7b1ad3991dd570
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216666"
---
# <a name="rename-import-attribute"></a>Zmień nazwę atrybutu importu

**C++Specjalne**

Działa wokół problemów z kolizją nazw.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **Zmień nazwę (** "*StaraNazwa*" **,** "*newname*" **)**

### <a name="parameters"></a>Parametry

*StaraNazwa*\
Stara nazwa w bibliotece typów.

*NewName*\
Nazwa, która ma być używana zamiast starej nazwy.

## <a name="remarks"></a>Uwagi

Po określeniu atrybutu **zmiany nazwy** kompilator zastępuje wszystkie wystąpienia elementu *StaraNazwa* w *bibliotece typów* z nazwą pliku w plikach nagłówkowych określoną przez użytkownika.

Atrybutu **zmiany nazwy** można użyć, gdy nazwa w bibliotece typów jest zgodna z definicją makra w plikach nagłówkowych systemu. Jeśli ta sytuacja nie zostanie rozwiązana, kompilator może wydać różne błędy składniowe, takie jak [błąd kompilatora C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) i [błąd kompilatora C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Zastąpienie dotyczy nazwy użytej w bibliotece typów, a nie nazwy użytej w pliku nagłówkowym.

Załóżmy na przykład, że właściwość o nazwie `MyParent` istnieje w bibliotece typów, a makro `GetMyParent` jest zdefiniowane w pliku nagłówkowym i używane wcześniej `#import`. Ponieważ `GetMyParent` jest to domyślna nazwa funkcji otoki dla właściwości obsługa `get` błędów, zostanie wystąpiła kolizja nazw. Aby obejść ten problem, użyj następującego atrybutu w `#import` instrukcji:

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

który zmienia `MyParent` nazwę w bibliotece typów. Próba zmiany `GetMyParent` nazwy otoki zakończy się niepowodzeniem:

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

Jest to spowodowane faktem `GetMyParent` , że nazwa występuje tylko w pliku nagłówkowym biblioteki typów.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
