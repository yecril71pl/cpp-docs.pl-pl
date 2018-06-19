---
title: Irowsetlocateimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: db8d0b5d81a53a71413998b39947eb71a1bd508a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111032"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl — Klasa
Implementuje OLE DB [irowsetlocate —](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interfejs, który pobiera dowolne wiersze z zestawu wierszy.  
  
## <a name="syntax"></a>Składnia

```cpp
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
       T,   
       RowsetInterface,   
       RowClass,   
       MapClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa pochodna od `IRowsetLocateImpl`.  
  
 `RowsetInterface`  
 Klasa pochodna od `IRowsetImpl`.  
  
 `RowClass`  
 Jednostki magazynu dla **HROW**.  
  
 `MapClass`  
 Jednostki magazynu dla wszystkich dojść do wierszy posiadanych przez dostawcę.  
  
 `BookmarkKeyType`  
 Typ zakładki, takie jak DŁUGI lub ciągiem. Zakładki zwykłej musi mieć długość co najmniej dwa bajty. (Długość jednobajtowe jest zarezerwowana dla OLE DB [standardowe zakładki](https://msdn.microsoft.com/en-us/library/ms712954.aspx)**DBBMK_FIRST**, **DBBMK_LAST**, i **DBBMK_INVALID**.)  
  
 `BookmarkType`  
 Mechanizm mapowania obsługi relacje zakładkę do danych.  
  
 `BookmarkMapClass`  
 Jednostki magazynu dla wszystkich dojść do wierszy w posiadaniu zakładki.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Compare](../../data/oledb/irowsetlocateimpl-compare.md)|Porównuje dwa zakładki.|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|Pobiera wiersze, zaczynając od określonej przez przesunięcie od zakładki wiersza.|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|Pobiera wiersze spełniające określony zakładki.|  
|[Wyznaczania wartości skrótu](../../data/oledb/irowsetlocateimpl-hash.md)|Zwraca wartość skrótu wartości dla określonego zakładek.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|Tablica zakładki.|  
  
## <a name="remarks"></a>Uwagi  
 `IRowsetLocateImpl` jest to implementacja szablony OLE DB [irowsetlocate —](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interfejsu. `IRowsetLocate` Służy do pobierania wierszy dowolnego z zestawu wierszy. Zestaw wierszy, który nie implementuje ten interfejs jest `sequential` zestawu wierszy. Gdy `IRowsetLocate` jest obecny w zestawie wierszy, kolumny 0 jest zakładki dla wierszy; odczytu w tej kolumnie uzyska wartość zakładki, która może służyć do zmiany położenia na tym samym wierszu.  
  
 `IRowsetLocateImpl` Służy do zaimplementowania Obsługa zakładek w dostawcy. Zakładki symboli zastępczych (indeksy w zestawie wierszy) umożliwiające konsumenta szybko powrócić do wiersza, dzięki czemu szybki dostęp do danych. Określa dostawcę, co zakładki może jednoznacznie zidentyfikować wiersza. Za pomocą `IRowsetLocateImpl` metod, możesz porównać zakładki, pobierania wierszy przez przesunięcie pobierania wierszy zakładką i zwracać wartości skrótów dla zakładek.  
  
 Obsługuje OLE DB zakładek w zestawie wierszy, aby wierszy pochodne względem tej klasy.  
  
 Aby uzyskać informacje dotyczące implementacji Obsługa zakładek, zobacz [dostawca obsługuje zakładek](../../data/oledb/provider-support-for-bookmarks.md) w *Visual C++ przewodnik* i [zakładki](https://msdn.microsoft.com/en-us/library/ms709728.aspx) w *OLE DB Podręcznik programisty* w zestawu SDK platformy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [Obsługa dostawców dla zakładek](../../data/oledb/provider-support-for-bookmarks.md)   
 [Zakładki](https://msdn.microsoft.com/en-us/library/ms709728.aspx)