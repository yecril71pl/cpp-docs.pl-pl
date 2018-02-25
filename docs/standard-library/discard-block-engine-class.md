---
title: "discard_block_engine — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::discard_block_engine
dev_langs:
- C++
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89cfd599f1f51c70f2e4ac108b32ccbe8bc6ae68
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="discardblockengine-class"></a>discard_block_engine — Klasa
Generuje losowe sekwencji odrzucając wartości zwracanych przez silnik podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Engine, size_t P, size_t R>  
class discard_block_engine;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Engine`  
 Typ podstawowy aparatu.  
  
 `P`  
 **Rozmiaru bloku**. Liczba wartości w każdym bloku.  
  
 `R`  
 **Blok używane**. Liczba wartości w każdym bloku, które są używane. Pozostałe zostaną odrzucone ( `P`  -  `R`). **Warunek wstępny**: `0 < R ≤ P`  
  
## <a name="members"></a>Elementy członkowskie  
  
||||  
|-|-|-|  
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|  
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|  
  
 Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu opisuje Adapter aparat tworzącego wartości odrzucając niektórych wartości zwracanych przez silnik podstawowej.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<losowe >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<losowe >](../standard-library/random.md)

