---
title: BEGIN_ACCESSOR — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ffb1d506a198586a5a625664f21c29954aada40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089848"
---
# <a name="beginaccessor"></a>BEGIN_ACCESSOR
Oznacza początek wpis dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```  
BEGIN_ACCESSOR(num, bAuto)  
```  
  
#### <a name="parameters"></a>Parametry  
 *num*  
 [in] Przesunięcie zero numer dostępu na tej mapie metody dostępu.  
  
 *bAuto*  
 [in] Określa, czy ta metoda dostępu jest akcesora automatycznej lub ręcznej metody dostępu. Jeśli **true**, akcesor jest automatycznie; Jeśli **false**, metody dostępu jest ręczne. Metody dostępu automatycznie oznacza, że pobierane dane dla Ciebie na operacji przenoszenia.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wielu metod dostępu w zestawie wierszy, należy określić `BEGIN_ACCESSOR_MAP` i użyj `BEGIN_ACCESSOR` makro dla każdego poszczególne metody dostępu. `BEGIN_ACCESSOR` Makro zostało zakończone z `END_ACCESSOR` makra. `BEGIN_ACCESSOR_MAP` Makro zostało zakończone z `END_ACCESSOR_MAP` makra.  
  
## <a name="example"></a>Przykład  
 Zobacz [begin_accessor_map —](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)