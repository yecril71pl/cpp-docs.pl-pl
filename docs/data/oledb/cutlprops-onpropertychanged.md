---
title: CUtlProps::OnPropertyChanged | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
dev_langs:
- C++
helpviewer_keywords:
- OnPropertyChanged method
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c9b52949db714206b6118000d004c6248b7d6235
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cutlpropsonpropertychanged"></a>CUtlProps::OnPropertyChanged
Wywołuje się po ustawieniu właściwości w celu obsługi łańcuchowa właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iCurSet`  
 Indeks tablicy właściwości zestawu; zero, jeśli istnieje tylko jedna właściwość.  
  
 `pDBProp`  
 Identyfikator właściwości i nową wartość w [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`. Zwraca wartość domyślna wartość to `S_OK`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli chcesz obsługiwać łańcuchowa właściwości, takie jak zakładki lub aktualizacje, których wartości są zależne od wartości właściwości innego, należy przesłonić tę funkcję.  
  
## <a name="example"></a>Przykład  
 W tej funkcji, użytkownik uzyskuje identyfikator właściwości z `DBPROP*` parametru. Teraz jest możliwe do porównania Identyfikatora przed właściwością łańcucha. W przypadku odnalezienia właściwość `SetProperties` jest wywoływana z właściwość, która będzie teraz można ustawić w połączeniu z innych właściwości. W tym przypadku, jeśli jeden pobiera `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, lub `DBPROP_ORDEREDBOOKMARKS` właściwość, jedną wartość `DBPROP_BOOKMARKS` właściwości.  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [CUtlProps, klasa](../../data/oledb/cutlprops-class.md)