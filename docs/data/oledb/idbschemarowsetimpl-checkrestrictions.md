---
title: IDBSchemaRowsetImpl::CheckRestrictions | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
dev_langs:
- C++
helpviewer_keywords:
- CheckRestrictions method
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab19a661e02bcfd0f5ca3730c69e22adfc3ae4db
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimplcheckrestrictions"></a>IDBSchemaRowsetImpl::CheckRestrictions
Sprawdza poprawność ograniczeń dla zestawu wierszy schematu.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT CheckRestrictions(REFGUID rguidSchema,  
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rguidSchema`  
 [in] Odwołanie do zestawu wierszy schematu żądany identyfikator GUID (na przykład `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [in] Liczba ograniczeń, które konsumenta przekazana dla zestawu wierszy schematu.  
  
 `rgRestrictions`  
 [in] Tablicy o długości *cRestrictions* ograniczenie wartości do ustawienia. Aby uzyskać więcej informacji, zobacz opis `rgRestrictions` parametru w [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CheckRestrictions` sprawdzania poprawności ograniczeń dla zestawu wierszy schematu. Sprawdza ograniczenia dotyczące `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, i **DBSCHEMA_PROVIDER_TYPES** zestawów wierszy schematu. Wywołać ją, aby ustalić, czy z klientem wywołanie **IDBSchemaRowset::GetRowset** jest poprawna. Do obsługi zestawów wierszy schematu wymienionych powyżej, należy utworzyć własny funkcja do wykonania tego zadania.  
  
 `CheckRestrictions` Określa, czy wywołuje konsumenta [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) z ograniczeń poprawne i prawidłowe ograniczenie typu (na przykład `VT_BSTR` ciągu) obsługującego dostawcę. Określa również, czy prawidłowy numer ograniczenia są obsługiwane. Domyślnie `CheckRestrictions` poprosi dostawcy, za pomocą [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) wywołania ograniczenia, które obsługuje w danym zestawie wierszy. Następnie porównuje ograniczenia od konsumenta z tymi, które jest obsługiwana przez dostawcę i powiedzie się lub kończy się niepowodzeniem.  
  
 Aby uzyskać więcej informacji dotyczących zestawów wierszy schematu, zobacz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w *OLE DB Podręcznik programisty* w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbschemarowsetimpl — klasa](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Elementy członkowskie idbschemarowsetimpl — klasa](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)