---
title: IDBSchemaRowsetImpl::SetRestrictions | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
dev_langs:
- C++
helpviewer_keywords:
- SetRestrictions method
ms.assetid: 707d5065-b853-4d38-9b67-3066b4d3b279
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b6effd432b033941d404c4935cdbad5a2336ac8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105858"
---
# <a name="idbschemarowsetimplsetrestrictions"></a>IDBSchemaRowsetImpl::SetRestrictions
Określa ograniczenia, które obsługuje w zestawie wierszy określonego schematu.  
  
## <a name="syntax"></a>Składnia  
  
```
void SetRestrictions(ULONG cRestrictions,  
  GUID* /* rguidSchema */,  
   ULONG* rgRestrictions);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRestrictions`  
 [in] Liczba ograniczeń w `rgRestrictions` tablicy i liczba identyfikatorów GUID w `rguidSchema` tablicy.  
  
 `rguidSchema`  
 [in] Tablica zestawów wierszy schematu, dla którego można pobrać ograniczeń identyfikatory GUID. Każdy element tablicy zawiera identyfikator GUID zestawu wierszy schematu jednego (na przykład `DBSCHEMA_TABLES`).  
  
 `rgRestrictions`  
 [in] Tablicy o długości `cRestrictions` ograniczenie wartości do ustawienia. Każdy element odpowiada ograniczenia dotyczące identyfikowany przez identyfikator GUID zestawu wierszy schematu. Jeśli zestawu wierszy schematu nie jest obsługiwana przez dostawcę, element ma ustawioną wartość zero. W przeciwnym razie **ULONG** wartość zawiera maska bitowa reprezentująca ograniczenia obsługiwane w tym zestaw wierszy schematu. Aby uzyskać więcej informacji, na którym ograniczenia odpowiadają wierszy określonego schematu, zapoznaj się spis zestaw wierszy schematu identyfikatorów GUID w [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w *OLE DB Podręcznik programisty* w systemie Windows ZESTAW SDK.  
  
## <a name="remarks"></a>Uwagi  
 **IDBSchemaRowset** obiektu wywołania `SetRestrictions` ustalenie, który ograniczeń obsługi w zestawie wierszy określonego schematu (jest ona wywoływana przez [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) za pośrednictwem upcasted wskaźnika). Ograniczenia Zezwalaj klientom pobieranie tylko pasujących wierszy (na przykład znaleźć wszystkie kolumny w tabeli "MyTable"). Ograniczenia są opcjonalne, a w przypadku, w których żaden nie jest obsługiwane (ustawienie domyślne), zwracane są wszystkie dane zawsze.  
  
 Domyślna implementacja tej metody ustawia `rgRestrictions` elementów na 0 w tablicy. Zastąpienie domyślnego w klasie sesji, aby ustawić ograniczenia inny niż domyślny.  
  
 Aby uzyskać informacje dotyczące implementacji Obsługa zestawów wierszy schematu, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).  
  
 Na przykład dostawcę, który obsługuje zestawów wierszy schematu zobacz [UpdatePV](../../visual-cpp-samples.md) próbki.  
  
 Aby uzyskać więcej informacji dotyczących zestawów wierszy schematu, zobacz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) w *OLE DB Podręcznik programisty* w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbschemarowsetimpl — klasa](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Elementy członkowskie idbschemarowsetimpl — klasa](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md)   
 [UpdatePV](../../visual-cpp-samples.md)