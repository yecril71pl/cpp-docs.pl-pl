---
title: Cdaorelationfieldinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRelationFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e53daaaa5ef4997762342cbfb74ae4d5fa96097d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo — Struktura
`CDaoRelationFieldInfo` Struktura zawiera informacje o polu w relacji zdefiniowany dla obiektów dostępu do danych (DAO).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoRelationFieldInfo  
{  
    CString m_strName;           // Primary  
    CString m_strForeignName;    // Primary  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Nazwa pola w tabeli podstawowej relacji.  
  
 `m_strForeignName`  
 Nazwa pola w tabeli obcego relacji.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt DAO relacji określa pola w tabeli podstawowej i pola w obcy tabeli, które definiują relację. Odwołania do głównej w definicji struktury powyżej wskazują, jak informacje zwracane w `m_pFieldInfos` członkiem [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) można uzyskać przez wywołanie obiektu [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo)funkcji członkowskiej klasy `CDaoDatabase`.  
  
 Klasy MFC nie obejmują relacji obiekty i pola relacji. Zamiast tego obiekt DAO obiektów MFC obiektów klasy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) zawiera kolekcję obiektów relacji, nazywany kolekcji relacji. Każdy obiekt relacji zawiera kolekcję obiektów pola relacji. Każdy obiekt pola relacji skorelowany pola w tabeli podstawowej za pomocą pola w tabeli obcego. Razem obiektów pól relacji zdefiniuj grupę pól w każdej tabeli, które definiują relację. `CDaoDatabase` zapewnia dostęp do obiektów relacji z `CDaoRelationInfo` obiektu przez wywołanie metody `GetRelationInfo` funkcję elementu członkowskiego. `CDaoRelationInfo` Obiektu, następnie jest elementem członkowskim danych `m_pFieldInfos`, który wskazuje tablicę `CDaoRelationFieldInfo` obiektów.  
  
 Wywołanie [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) funkcji członkowskiej klasy zawierający `CDaoDatabase` obiekt, w których relacje kolekcji jest przechowywane obiektu relacji w. Następnie dostępu `m_pFieldInfos` członkiem [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) obiektu. `CDaoRelationFieldInfo` definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoRelationFieldInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Struktura CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md)
