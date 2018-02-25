---
title: IConvertTypeImpl::CanConvert | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
dev_langs:
- C++
helpviewer_keywords:
- CanConvert method
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6431878d94c4dde469a23808b01381c88a2b33ec
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="iconverttypeimplcanconvert"></a>IConvertTypeImpl::CanConvert
Zapewnia informacje o dostępności konwersje typów polecenia lub w zestawie wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(CanConvert)(DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="remarks"></a>Uwagi  
 Używa konwersji danych OLE DB w `MSADC.DLL`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [IConvertTypeImpl, klasa](../../data/oledb/iconverttypeimpl-class.md)