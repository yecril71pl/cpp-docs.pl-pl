---
title: "discard_block_engine — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: random/std::discard_block_engine
dev_langs: C++
helpviewer_keywords: discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b5163956cf2c8bd2fd258adf1fcde7c038d15f69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 **Blok używane**. Liczba wartości w każdym bloku, które są używane. Pozostałe zostaną odrzucone ( `P`  -  `R`). **Warunek wstępny**:`0 < R ≤ P`  
  
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

