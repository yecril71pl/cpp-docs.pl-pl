---
title: "Cdaoindexfieldinfo — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b745a6f450bdf96389f49c673dc623b614e04db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo — Struktura
`CDaoIndexFieldInfo` Struktura zawiera informacje dotyczące obiektu pola indeksu zdefiniowany dla obiektów dostępu do danych (DAO).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoIndexFieldInfo  
{  
    CString m_strName;          // Primary  
    BOOL m_bDescending;         // Primary  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Unikatowej nazwy obiektu pola indeksu. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 *m_bDescending*  
 Wskazuje indeks kolejność zdefiniowane przez obiekt indeksu. **Wartość TRUE,** Jeśli kolejność jest malejąco.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt indeksu może mieć wiele pól i wskazujący pola, które jest zindeksowane tabledef (lub zestawu rekordów z tabeli). Odwołania do podstawowych powyżej wskazują, jak informacje zwracane w `m_pFieldInfos` członkiem [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) można uzyskać przez wywołanie obiektu `GetIndexInfo` funkcji członkowskiej klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Klasy MFC nie obejmują obiekty indeks i indeks pola. Zamiast tego obiekt DAO obiektów MFC obiektów klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) lub [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) zawiera kolekcję obiektów indeksu, nazywanych kolekcji indeksów. Każdy obiekt indeksu zawiera kolekcję obiektów pola. Te klasy podać funkcji elementów członkowskich, aby uzyskiwać dostęp do poszczególnych elementów informacji indeksu lub uzyskać dostępu do nich jednocześnie z `CDaoIndexInfo` obiektu przez wywołanie metody `GetIndexInfo` funkcji członkowskiej krawędzi zawierającego go obiektu. `CDaoIndexInfo` Obiektu, następnie jest elementem członkowskim danych `m_pFieldInfos`, który wskazuje tablicę `CDaoIndexFieldInfo` obiektów.  
  
 Wywołanie `GetIndexInfo` funkcji członkowskiej zawierającego obiektu tabledef lub zestawu rekordów, w której indeksy kolekcja jest przechowywany obiekt indeksu planuje się. Następnie dostępu `m_pFieldInfos` członkiem [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) obiektu. Długość `m_pFieldInfos` tablicy są przechowywane w `m_nFields`. `CDaoIndexFieldInfo`definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoIndexFieldInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

