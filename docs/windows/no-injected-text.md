---
title: no_injected_text | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74336ffaa5e1f9f1990acedf1669526c9152b82b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880351"
---
# <a name="noinjectedtext"></a>no_injected_text
Zabezpiecza kompilator przed wstrzyknięcie kodu w wyniku użycia atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ no_injected_text(  
   boolean  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 `boolean`(opcjonalnie)  
 **wartość true,** Jeśli chcesz, aby żaden kod dodane **false** do umożliwia ich wstrzyknięcie kodu. **wartość true,** jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 Najczęściej używane **no_injected_text** jest atrybut C++ [/Fx](../build/reference/fx-merge-injected-code.md) opcję kompilatora, która wstawia **no_injected_text** atrybut do pliku .mrg.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty kompilatora](../windows/compiler-attributes.md)   
