---
title: zmień nazwę (#import)
ms.date: 10/18/2018
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 0fbed04f040a47b5b389f40eeb15254da4a7940b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179733"
---
# <a name="rename-import"></a>Zmień nazwę (\#importowanie)

**Określonego język C++**

Działania dotyczące problemów kolizji nazw.

## <a name="syntax"></a>Składnia

```
rename("OldName","NewName")
```

### <a name="parameters"></a>Parametry

*OldName*<br/>
Stara nazwa w bibliotece typów.

*Nowa nazwa*<br/>
Nazwa ma być używana zamiast starej nazwy.

## <a name="remarks"></a>Uwagi

Jeśli ten atrybut jest określony, kompilator zamienia wszystkie wystąpienia *StaraNazwa* w bibliotece typów, przy użyciu podanego użytkownika *NewName* w wynikowej plikach nagłówkowych.

Ten atrybut może być używany, gdy nazwy w bibliotece typów pokrywa się z definicji makra w plikach nagłówkowych systemu. Jeśli ta sytuacja nie uda się rozwiązać, a następnie różne błędy składniowe zostanie wygenerowany, takich jak [błąd kompilatora C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) i [błąd kompilatora C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Zastąpienie jest nazwę w bibliotece typów nie nazwa używana w powstałym pliku nagłówka.

Na przykład, załóżmy, że właściwość o nazwie `MyParent` znajduje się w bibliotece typów i makra `GetMyParent` jest zdefiniowana w pliku nagłówkowym i używana przed `#import`. Ponieważ `GetMyParent` jest domyślna nazwa funkcji otoku obsługi błędów `get` kolizji nazw właściwości, zostanie przeprowadzona. Aby obejść ten problem, należy użyć następujący atrybut w `#import` instrukcji:

```cpp
rename("MyParent","MyParentX")
```

który zmienia nazwę `MyParent` w bibliotece typów. Próba zmiany nazwy `GetMyParent` nazwa otoki zakończy się niepowodzeniem:

```cpp
rename("GetMyParent","GetMyParentX")
```

Jest to spowodowane nazwę `GetMyParent` występuje tylko w wynikowy plik nagłówkowy biblioteki typów.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)