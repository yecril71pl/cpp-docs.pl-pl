---
title: Zmień nazwę atrybutu importu
ms.date: 08/29/2019
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 520369f0308078fead2947e27a512f25a3ad3fab
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447484"
---
# <a name="rename-import-attribute"></a>Zmień nazwę atrybutu importu

**C++Specjalne**

Działa wokół problemów z kolizją nazw.

## <a name="syntax"></a>Składnia

> **#import** **zmianę nazwy** *biblioteki typów* ("*StaraNazwa*" **,** "*newname*" **)**

### <a name="parameters"></a>Parametry

*Staranazwa*\
Stara nazwa w bibliotece typów.

*NewName*\
Nazwa, która ma być używana zamiast starej nazwy.

## <a name="remarks"></a>Uwagi

Po określeniu atrybutu **zmiany nazwy** kompilator zastępuje wszystkie wystąpienia elementu *StaraNazwa* w *bibliotece typów* z nazwą *pliku w plikach* nagłówkowych określoną przez użytkownika.

Atrybutu **zmiany nazwy** można użyć, gdy nazwa w bibliotece typów jest zgodna z definicją makra w plikach nagłówkowych systemu. Jeśli ta sytuacja nie zostanie rozwiązana, kompilator może wydać różne błędy składniowe, takie jak [błąd kompilatora C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) i [błąd kompilatora C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Zastąpienie dotyczy nazwy użytej w bibliotece typów, a nie nazwy użytej w pliku nagłówkowym.

Załóżmy na przykład, że właściwość o nazwie `MyParent` istnieje w bibliotece typów, a makro `GetMyParent` jest zdefiniowane w pliku nagłówkowym i używane przed `#import`. Ponieważ `GetMyParent` jest domyślną nazwą funkcji otoki dla właściwości `get` obsługi błędów, występuje kolizja nazw. Aby obejść ten problem, użyj następującego atrybutu w instrukcji `#import`:

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

który zmienia nazwę `MyParent` w bibliotece typów. Próba zmiany nazwy `GetMyParent` otoki zakończy się niepowodzeniem:

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

Jest to spowodowane tym, że nazwa `GetMyParent` występuje tylko w pliku nagłówkowym biblioteki typów.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz też

[#import atrybuty](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
