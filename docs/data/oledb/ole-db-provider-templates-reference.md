---
title: Szablony dostawców OLE DB — kompendium
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: f0200f0cff5292a75ec853496a644c148c8356a3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446067"
---
# <a name="ole-db-provider-templates-reference"></a>Szablony dostawców OLE DB — kompendium

Klasy i interfejsy szablonów dostawców OLE DB mogą być pogrupowane w następujące kategorie. Materiał referencyjny zawiera również informacje o [makrach dla szablonów dostawców OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).

Klasy korzystają z następującej konwencji nazewnictwa: Klasa o nazwie z wzorcem `IWidgetImpl` zapewnia implementację interfejsu `IWidget`.

## <a name="session-classes"></a>Klasy sesji

[IDBCreateSessionImpl —](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Tworzy nową sesję z obiektu źródła danych i zwraca żądany interfejs w nowo utworzonej sesji. Obowiązkowy interfejs dla obiektów źródła danych.

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Implementuje właściwości sesji przez wywołanie funkcji statycznej zdefiniowanej przez mapę właściwości. W klasie sesji należy określić mapę zestawu właściwości. Obowiązkowy interfejs w sesjach.

## <a name="rowset-classes"></a>Klasy zestawu wierszy

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

Zapewnia standardową implementację zestawu wierszy OLE DB, bez konieczności dziedziczenia wielu interfejsów implementacji. Jedyną metodą, dla której należy podać implementację, jest `Execute`.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Udostępnia implementację domyślną dla uchwytu wiersza, który jest używany w klasie `IRowsetImpl`. Dojście do wiersza jest logicznie unikatowym tagiem dla wiersza wynikowego. `IRowsetImpl` tworzy nowy `CSimpleRow` dla każdego wiersza żądanego w `IRowsetImpl::GetNextRows`.

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB wymaga od dostawców zaimplementowania `HACCESSOR`, który jest tagiem tablicy struktur `DBBINDING`. Dostarcza `HACCESSOR`s, które są adresami struktur `BindType`. Obowiązkowe dla zestawów wierszy i poleceń.

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Deleguje do funkcji statycznej zdefiniowanej przez mapę kolumn dostawcy. Obowiązkowy interfejs dla zestawów wierszy i poleceń.

[IConvertTypeImpl —](../../data/oledb/iconverttypeimpl-class.md)<br/>
Podaje informacje o dostępności konwersji typu dla polecenia lub zestawu wierszy. Obowiązkowe dla poleceń, zestawów wierszy i zestawów wierszy indeksu. Implementuje interfejs `IConvertType` przez delegowanie do obiektu konwersji dostarczonego przez OLE DB.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implementuje interfejs `IDBSchemaRowset` i funkcję szablonowana Creator `CreateSchemaRowset`.

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Otwiera i zwraca zestaw wierszy, który zawiera wszystkie wiersze z pojedynczej tabeli bazowej lub indeksu. Obowiązkowy interfejs dla obiektu sesji.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implementuje interfejs OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) , który umożliwia aktualizowanie wartości kolumn w istniejących wierszach, usuwanie wierszy i wstawianie nowych wierszy.

[IRowsetCreatorImpl —](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Ta klasa dziedziczy z [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) i przesłania [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` wykonuje te same funkcje co `IObjectWithSite`, ale również włącza OLE DB właściwości `DBPROPCANSCROLLBACKWARDS` i `DBPROPCANFETCHBACKWARDS`.

[IRowsetIdentityImpl —](../../data/oledb/irowsetidentityimpl-class.md)<br/>
Implementuje interfejs `IRowsetIdentity`, który umożliwia porównanie, czy dwa wiersze danych są identyczne.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
Zapewnia implementację interfejsu `IRowset`, który jest podstawowym interfejsem zestawu wierszy.

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implementuje właściwości zestawu wierszy przy użyciu mapy zestawu właściwości zdefiniowanej w klasie poleceń. Obowiązkowy interfejs w zestawach wierszy.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implementuje interfejs OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , który pobiera dowolne wiersze z zestawu wierszy. Aby można było obsługiwać zakładki OLE DB w zestawie wierszy, należy uczynić zestaw wierszy Dziedziczony z tej klasy.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implementuje funkcje emisji, aby doradzać odbiornikom w punkcie połączenia `IID_IRowsetNotify` zmian zawartości zestawu wierszy. Konsumenci, którzy obsługują powiadomienia, implementują [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) i rejestrują się w tym punkcie połączenia.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implementuje interfejs OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) , który umożliwia konsumentom opóźnienie przekazywania zmian wprowadzonych z [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) do źródła danych i cofanie zmian przed przekazaniem.

## <a name="command-classes"></a>Klasy poleceń

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
Zapewnia implementację interfejsu `ICommand`. Ten interfejs nie jest widoczny, ale jest obsługiwany przez `ICommandTextImpl`. Obowiązkowy interfejs w obiekcie Command.

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Ta implementacja interfejsu `ICommandProperties` jest udostępniana przez funkcję statyczną zdefiniowaną przez makro `BEGIN_PROPSET_MAP`. Obowiązkowe dla poleceń.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Ustawia, przechowuje i zwraca tekst polecenia. Obowiązkowe dla poleceń.

[IDBCreateCommandImpl —](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Tworzy nowe polecenie z obiektu Session i zwraca żądany interfejs na nowo utworzonym poleceniu. Opcjonalny interfejs dla obiektów sesji.

Inne klasy poleceń są `IColumnsInfoImpl` i `IAccessorImpl`, opisane w powyższej sekcji klasy zestawu wierszy.

## <a name="data-source-classes"></a>Klasy źródeł danych

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
Tworzy i usuwa połączenie z klientem. Obowiązkowy interfejs dla obiektów źródła danych i opcjonalny interfejs w modułach wyliczających.

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` jest obowiązkowy interfejs dla obiektów źródła danych i opcjonalny interfejs dla modułów wyliczających. Jeśli jednak moduł wyliczający ujawnia `IDBInitialize`, musi uwidaczniać `IDBProperties` (właściwości źródła danych).

[IGetDataSourceImpl —](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Uzyskuje wskaźnik interfejsu do obiektu źródła danych. Obowiązkowy interfejs w sesji.

## <a name="other-classes"></a>Inne klasy

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
Implementuje właściwości dla różnych OLE DB interfejsów właściwości (na przykład `IDBProperties`, `ISessionProperties`i `IRowsetInfo`).

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

Implementuje interfejs OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) , Dodawanie rekordów do i pobieranie rekordów z elementu członkowskiego danych.

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Szablony OLE DB](../../data/oledb/ole-db-templates.md)