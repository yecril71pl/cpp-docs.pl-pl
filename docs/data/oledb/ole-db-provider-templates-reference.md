---
title: Szablony dostawcy OLE DB dokumentacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7832985c6095aecae5098461d36947ff4268d262
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465339"
---
# <a name="ole-db-provider-templates-reference"></a>Szablony dostawców OLE DB — kompendium
Klasy i interfejsy dla szablony OLE DB Provider można podzielić na następujące kategorie. Materiały referencyjne zawiera również informacje o [makra szablony OLE DB Provider](../../data/oledb/macros-for-ole-db-provider-templates.md).  
  
 Klasy, użyj następującej konwencji nazewnictwa: klasa o nazwie za pomocą wzorca `IWidgetImpl` będzie zapewniać implementację interfejsu `IWidget`.  
  
## <a name="session-classes"></a>Klasy sesji  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzoną sesji. Obowiązkowego interfejsu na obiekty źródła danych.  
  
 [Isessionpropertiesimpl —](../../data/oledb/isessionpropertiesimpl-class.md)  
 Implementuje właściwości sesji, wywołując funkcję statyczną, zdefiniowane przez mapowanie zestawu właściwości. Mapa zestawu właściwości powinny być określone w swojej klasy sesji. Obowiązkowego interfejsu w ramach sesji.  
  
## <a name="rowset-classes"></a>Klasy zestawów wierszy  
 [Crowsetimpl —](../../data/oledb/crowsetimpl-class.md)  
  
 Zapewnia standardową implementację zestawu wierszy OLE DB bez konieczności wielokrotnego dziedziczenia wiele implementacji interfejsów. Jedyną metodą, dla którego należy podać implementacja jest `Execute`.  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 Udostępnia domyślną implementację dla dojście do wiersza, który jest używany w `IRowsetImpl` klasy. Dojście do wiersza jest logicznie unikatowych tagów na podstawie wyniku wiersza. `IRowsetImpl` Tworzy nową `CSimpleRow` dla każdego wiersza w wymagane `IRowsetImpl::GetNextRows`.  
  
 [Iaccessorimpl —](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB wymaga dostawcy zaimplementować `HACCESSOR`, który jest tag do tablicy `DBBINDING` struktury. Udostępnia `HACCESSOR`s, które są adresy `BindType` struktury. Obowiązkowe na polecenia i zestawy wierszy.  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 Delegaty do statycznej funkcji zdefiniowane przez mapowanie kolumn w dostawcy. Obowiązkowego interfejsu na polecenia i zestawy wierszy.  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 Udostępnia informacje o dostępności konwersje typów dotyczącą polecenia lub w zestawie wierszy. Obowiązkowe w poleceń, zestawy wierszy i zestawy wierszy indeksu. Implementuje `IConvertType` interfejsu przez delegowanie do konwersji obiektu pochodzącego z OLE DB.  
  
 [Idbschemarowsetimpl —](../../data/oledb/idbschemarowsetimpl-class.md)  
 Implementuje `IDBSchemaRowset` interfejsu i funkcja szablonowej twórcy `CreateSchemaRowset`.  
  
 [Iopenrowsetimpl —](../../data/oledb/iopenrowsetimpl-class.md)  
 Zostanie otwarty i zwraca zestawu wierszy, który zawiera wszystkie wiersze z jednej tabeli bazowej lub indeksu. Obowiązkowego interfejsu dla obiektu sesji.  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 Implementuje OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)) interfejs, który umożliwia aktualizowanie wartości kolumn w istniejących wierszy: usuwanie wierszy, a następnie wstawianie nowych wierszy.  
  
 [Irowsetcreatorimpl —](../../data/oledb/irowsetcreatorimpl-class.md)  
 Ta klasa dziedziczy [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) i zastępuje [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). `IRowsetCreatorImpl` wykonuje te same funkcje co `IObjectWithSite` , lecz także właściwości OLE DB `DBPROPCANSCROLLBACKWARDS` i `DBPROPCANFETCHBACKWARDS`.  
  
 [Irowsetidentityimpl —](../../data/oledb/irowsetidentityimpl-class.md)  
 Implementuje `IRowsetIdentity` interfejs, który umożliwia porównanie, czy dwa wiersze danych są identyczne, czy nie.  
  
 [Irowsetimpl —](../../data/oledb/irowsetimpl-class.md)  
 Udostępnia implementację `IRowset` interfejs, który jest interfejsem podstawowy zestaw wierszy.  
  
 [Irowsetinfoimpl —](../../data/oledb/irowsetinfoimpl-class.md)  
 Implementuje właściwości zestawu wierszy za pomocą właściwości ustaw mapy zdefiniowany w klasie polecenia. Obowiązkowego interfejsu na zestawów wierszy.  
  
 [Irowsetlocateimpl —](../../data/oledb/irowsetlocateimpl-class.md)  
 Implementuje OLE DB [irowsetlocate —](/previous-versions/windows/desktop/ms721190\(v=vs.85\)) interfejs, który pobiera wiersze z dowolnego z zestawu wierszy. Aby zapewnić obsługę OLE DB zakładki w zestawie wierszy, należy pochodne względem tej klasy zestawu wierszy.  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 Implementuje funkcje, które można wykonać funkcji advise odbiorników dla punktu połączenia można rozgłaszać `IID_IRowsetNotify` zmian zawartości zestawu wierszy. Implementowanie odbiorców, którzy obsługi powiadomień [IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\)) i zarejestrować ją w tym punkcie połączenia.  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 Implementuje OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401\(v=vs.85\)) interfejs, który umożliwia opóźnienie transmisji w trybie zmiany wprowadzone za pomocą [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)) do źródła danych i Cofnij zmiany przed rozpoczęciem transmisji.  
  
## <a name="command-classes"></a>Klasy poleceń  
 [Icommandimpl —](../../data/oledb/icommandimpl-class.md)  
 Udostępnia implementację `ICommand` interfejsu. Ten interfejs nie jest widoczny, ale jest obsługiwany przez `ICommandTextImpl`. Obowiązkowego interfejsu dla obiektu polecenia.  
  
 [Icommandpropertiesimpl —](../../data/oledb/icommandpropertiesimpl-class.md)  
 Ta implementacja `ICommandProperties` interfejsu są dostarczane przez funkcję statyczną, zdefiniowane przez `BEGIN_PROPSET_MAP` makra. Obowiązkowe w poleceniach.  
  
 [Icommandtextimpl —](../../data/oledb/icommandtextimpl-class.md)  
 Ustawia, przechowuje i zwraca tekst polecenia. Obowiązkowe w poleceniach.  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 Tworzy nowe polecenie z obiektu session i zwraca żądanego interfejsu na nowo utworzony polecenia. Opcjonalny interfejs dla obiektów sesji.  
  
 Inne klasy polecenia są `IColumnsInfoImpl` i `IAccessorImpl`, które zostały opisane w powyższej sekcji klasy zestawów wierszy.  
  
## <a name="data-source-classes"></a>Klasy źródła danych  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 Tworzy i usuwa połączenie z konsumenta. Obowiązkowego interfejsu na obiekty źródła danych i opcjonalnie interfejsu na modułach wyliczających.  
  
 [Idbpropertiesimpl —](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` jest obowiązkowego interfejsu dla obiekty źródła danych i opcjonalny interfejs dla modułów wyliczających. Jednakże jeśli moduł wyliczający udostępnia `IDBInitialize`, musi uwidaczniać `IDBProperties` (właściwości w źródle danych).  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 Uzyskuje wskaźnik interfejsu do obiektu źródła danych. Obowiązkowego interfejsu sesji.  
  
## <a name="other-classes"></a>Inne klasy  
 [Cutlprops —](../../data/oledb/cutlprops-class.md)  
 Implementuje właściwości dla różnych interfejsów właściwość OLE DB (na przykład `IDBProperties`, `ISessionProperties`, i `IRowsetInfo`).  
  
 [Ierrorrecordsimpl —](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 Implementuje OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) interfejsu, dodawanie rekordów do i pobierania rekordów z element członkowski danych.  
  
## <a name="see-also"></a>Zobacz też  
 [OLE DB — Kompendium szablonów konsumentów](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Szablony OLE DB](../../data/oledb/ole-db-templates.md)