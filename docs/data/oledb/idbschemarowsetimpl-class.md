---
title: "Idbschemarowsetimpl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBSchemaRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBSchemaRowsetImpl class
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: db5af177ead206c6546b5377ac7f94fdc331f53a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl — Klasa
Udostępnia implementację dla zestawów wierszy schematu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `SessionClass`  
 Klasa za pomocą którego `IDBSchemaRowsetImpl` jest dziedziczona. Ta klasa będzie zazwyczaj klasy sesji użytkownika.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)|Sprawdza poprawność ograniczeń dla zestawu wierszy schematu.|  
|[CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)|Implementuje funkcję twórcy obiektu COM dla obiekt określony przez parametr szablonu.|  
|[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)|Określa ograniczenia, które obsługuje w zestawie wierszy określonego schematu.|  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)|Zwraca zestaw wierszy schematu.|  
|[GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)|Zwraca listę zestawów wierszy schematu dostępne dla [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa implementuje [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) interfejsu i funkcja twórcy szablonowej [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).  
  
 OLE DB używa zestawów wierszy schematu, aby zwrócić dane o danych dostawcy. Tych danych jest często nazywana "metadanych". Domyślnie przez dostawcę musi obsługiwać zawsze `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, i **DBSCHEMA_PROVIDER_TYPES**, zgodnie z opisem w [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w  *OLE DB Podręcznik programisty*. Zestawy wierszy schematu są określone w mapie schematu. Aby uzyskać informacji na temat wpisów map schematu, zobacz [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).  
  
 OLE DB Provider kreatora, w Kreatorze obiektu ATL automatycznie generuje kod dla zestawów wierszy schematu w projekcie. (Domyślnie, Kreator obsługuje zestawy wierszy schematu obowiązkowe powyżej). Podczas tworzenia konsumenta za pomocą Kreatora obiekt ATL, kreator używa zestawów wierszy schematu do powiązania danych do dostawcy. Jeśli nie implementuje z zestawów wierszy schematu, aby zapewnić prawidłowe metadane, Kreator nie zostanie powiązana prawidłowe dane.  
  
 Aby uzyskać informacje na temat sposobu obsługi zestawów wierszy schematu w dostawcy, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).  
  
 Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [zestawów wierszy schematu](https://msdn.microsoft.com/en-us/library/ms712921.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy członkowskie idbschemarowsetimpl — klasa](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md)