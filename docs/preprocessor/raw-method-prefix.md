---
title: raw_method_prefix
ms.date: 03/27/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 963e04752dcb797343550d9b89f778bfe0e8a593
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021414"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**Określonego język C++**

Określa różne prefiks, aby uniknąć konfliktów nazw.

## <a name="syntax"></a>Składnia

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>Parametry

*Prefiks*<br/>
Prefiks który ma być używany.

## <a name="remarks"></a>Uwagi

Niskiego poziomu właściwości i metod, które są dostępne w funkcji elementów członkowskich o nazwie z prefiksem domyślne **raw_** Aby uniknąć konfliktów nazw z wysokiego poziomu funkcji elementów członkowskich obsługi błędów.

> [!NOTE]
> Efekty **raw_method_prefix —** atrybutu nie zostaną zmienione przez obecność [raw_interfaces_only —](raw-interfaces-only.md) atrybutu. **Raw_method_prefix —** zawsze pierwszeństwo przed `raw_interfaces_only` w określenie prefiksu. Jeśli oba atrybuty są używane w tym samym `#import` instrukcji, a następnie prefiksu określonego przez **raw_method_prefix —** atrybut jest używany.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)