---
title: raw_method_prefix
ms.date: 10/18/2018
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 4169b4e23049bf1cf2c61eaefba619169e0ce377
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467774"
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
> Efekty **raw_method_prefix —** atrybutu nie zostaną zmienione przez obecność [raw_interfaces_only —](#_predir_raw_interfaces_only) atrybutu. **Raw_method_prefix —** zawsze pierwszeństwo przed `raw_interfaces_only` w określenie prefiksu. Jeśli oba atrybuty są używane w tym samym `#import` instrukcji, a następnie prefiksu określonego przez **raw_method_prefix —** atrybut jest używany.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)