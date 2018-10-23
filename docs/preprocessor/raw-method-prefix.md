---
title: raw_method_prefix — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78094053c963f5d836646e91857e171625c447c9
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808553"
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