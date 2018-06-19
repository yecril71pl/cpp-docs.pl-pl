---
title: CRowsetImpl::GetColumnInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- GetColumnInfo method
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a989b31d672c9019d2ed5e61490f4e0042ab4c47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096470"
---
# <a name="crowsetimplgetcolumninfo"></a>CRowsetImpl::GetColumnInfo
Pobiera informacje dotyczące kolumn dla żądania określonego klienta.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,  
   ULONG* pcCols);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pv`  
 [in] Wskaźnik do użytkownika `CRowsetImpl` klasy.  
  
 `pcCols`  
 [in] Wskaźnik (output), do liczby kolumn zwracana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do statycznego **ATLCOLUMNINFO** struktury.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zastąpienie zaawansowane.  
  
 Ta metoda jest wywoływana przez kilka podstawowa Implementacja klasy można pobrać informacji o kolumnie dla żądania określonego klienta. Zwykle tę metodę można wywołać `IColumnsInfoImpl`. Jeśli przesłonić tę metodę, należy umieścić wersję metody w Twojej `CRowsetImpl`-klasy. Ponieważ metoda może być umieszczany w klasie innej niż — którego ma zastosowany szablon, należy zmienić `pv` do odpowiedniego `CRowsetImpl`-klasy.  
  
 W poniższym przykładzie pokazano **w GetColumnInfo** użycia. W tym przykładzie **CMyRowset** jest `CRowsetImpl`-klasy. Aby zastąpić `GetColumnInfo` dla wszystkich wystąpień tej klasy, umieść w następującej metody **CMyRowset** definicji klasy:  
  
 [!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRowsetImpl, klasa](../../data/oledb/crowsetimpl-class.md)