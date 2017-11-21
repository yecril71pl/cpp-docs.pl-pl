---
title: CRowsetImpl::GetColumnInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetColumnInfo
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
dev_langs: C++
helpviewer_keywords: GetColumnInfo method
ms.assetid: 9ef76525-f996-4c6f-81b9-68eb260350ef
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1229a9f45d7bd0f4a2f80b8443179640cd9f8926
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetimplgetcolumninfo"></a>CRowsetImpl::GetColumnInfo
Pobiera informacje dotyczące kolumn dla żądania określonego klienta.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(  
   T* pv,  
   ULONG* pcCols   
);  
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
 [Crowsetimpl — klasa](../../data/oledb/crowsetimpl-class.md)