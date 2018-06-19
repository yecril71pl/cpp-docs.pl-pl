---
title: Dokumentacja szablonów OLE DB Provider | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 040e8a5e244b7978a2b9ead394e243207939655c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112423"
---
# <a name="ole-db-provider-templates-reference"></a>Szablony dostawców OLE DB — kompendium
Klasy i interfejsy dla OLE DB szablonów dostawców można podzielić na następujące kategorie. Materiałów referencyjnych zawiera także informacje o [makra dla szablony OLE DB Provider](../../data/oledb/macros-for-ole-db-provider-templates.md).  
  
 Klasy, użyj następującej konwencji nazewnictwa: klasa o nazwie przy użyciu wzorca **IWidgetImpl** może zapewniać implementację interfejsu **IWidget**.  
  
## <a name="session-classes"></a>Klasy sesji  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 Tworzy nową sesję z obiektu źródła danych i zwraca żądanego interfejsu na nowo utworzony sesji. Obowiązkowego interfejsu na obiekty źródła danych.  
  
 [Isessionpropertiesimpl —](../../data/oledb/isessionpropertiesimpl-class.md)  
 Implementuje właściwości sesji przez wywołanie metody statycznej funkcji zdefiniowanej przez mapę zestawu właściwości. Mapa zestaw właściwości powinny być określone w klasie sesji. Obowiązkowego interfejsu na sesji.  
  
## <a name="rowset-classes"></a>Klasy zestawów wierszy  
 [Crowsetimpl —](../../data/oledb/crowsetimpl-class.md)  
  
 Udostępnia standardowej implementacji zestawu wierszy OLE DB bez konieczności dziedziczenie wielokrotne wiele implementacji interfejsów. Jedyną metodą, dla której należy podać implementacja jest **Execute**.  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 Udostępnia domyślną implementację dla dojście do wiersza, który jest używany w `IRowsetImpl` klasy. Dojście do wiersza jest logicznie unikatowy tag dla wiersza wynik. `IRowsetImpl` Tworzy nowy `CSimpleRow` dla każdego wiersza w wymagane `IRowsetImpl::GetNextRows`.  
  
 [Iaccessorimpl —](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB wymaga dostawców do zaimplementowania **HACCESSOR**, która jest tag do tablicy **DBBINDING** struktury. Udostępnia **HACCESSOR**, które są adresy **BindType** struktury. Obowiązkowe na polecenia i zestawy wierszy.  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 Obiekty delegowane do statycznych funkcji zdefiniowanej przez dostawcę mapowania kolumn. Obowiązkowego interfejsu na polecenia i zestawy wierszy.  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 Zapewnia informacje o dostępności konwersje typów polecenia lub w zestawie wierszy. Obowiązkowe poleceń, zestawy wierszy i zestawy wierszy indeksu. Implementuje **IConvertType** interfejsu przez delegowanie do obiektu konwersji dostarczonych przez OLE DB.  
  
 [Idbschemarowsetimpl —](../../data/oledb/idbschemarowsetimpl-class.md)  
 Implementuje **IDBSchemaRowset** interfejsu i funkcja twórcy szablonowej `CreateSchemaRowset`.  
  
 [Iopenrowsetimpl —](../../data/oledb/iopenrowsetimpl-class.md)  
 Otwiera i zwraca zestaw wierszy, która obejmuje wszystkie wiersze z jednej tabeli podstawowej lub indeks. Obowiązkowego interfejsu dla obiekt sesji.  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 Implementuje OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) interfejs, który umożliwia aktualizowania wartości kolumn w istniejących wierszy, usuwanie wierszy i wstawiania nowych wierszy.  
  
 [Irowsetcreatorimpl —](../../data/oledb/irowsetcreatorimpl-class.md)  
 Ta klasa dziedziczy [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) i zastępuje [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). `IRowsetCreatorImpl` wykonuje te same funkcje jak `IObjectWithSite` , lecz także właściwości OLE DB **DBPROPCANSCROLLBACKWARDS** i **DBPROPCANFETCHBACKWARDS**.  
  
 [Irowsetidentityimpl —](../../data/oledb/irowsetidentityimpl-class.md)  
 Implementuje **IRowsetIdentity** interfejs, który umożliwia porównanie, czy dwa wiersze danych są identyczne, czy nie.  
  
 [Irowsetimpl —](../../data/oledb/irowsetimpl-class.md)  
 Udostępnia implementację elementu `IRowset` interfejsu, który jest interfejs podstawowy zestaw wierszy.  
  
 [Irowsetinfoimpl —](../../data/oledb/irowsetinfoimpl-class.md)  
 Implementuje właściwości zestawu wierszy za pomocą właściwości ustaw mapy zdefiniowany w klasie polecenia. Obowiązkowego interfejsu na zestawów wierszy.  
  
 [Irowsetlocateimpl —](../../data/oledb/irowsetlocateimpl-class.md)  
 Implementuje OLE DB [irowsetlocate —](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interfejs, który pobiera dowolne wiersze z zestawu wierszy. Obsługuje OLE DB zakładek w zestawie wierszy, aby wierszy pochodne względem tej klasy.  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 Implementuje emisji funkcji w celu poinformowania odbiorników w punkcie połączenia **IID_IRowsetNotify** zmian zawartości zestawu wierszy. Implementowanie konsumentów, które obsługują powiadomienia [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) i zarejestruj go w tym punkcie połączenia.  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 Implementuje OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) interfejs, który umożliwia opóźnienia przekazania zmiany wprowadzone w [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) do źródła danych, a Cofnij zmiany przed ich przesłaniem.  
  
## <a name="command-classes"></a>Klasy poleceń  
 [Icommandimpl —](../../data/oledb/icommandimpl-class.md)  
 Udostępnia implementację elementu `ICommand` interfejsu. Ten interfejs nie jest widoczne, ale jest obsługiwany przez **icommandtextimpl —**. Obowiązkowego interfejsu dla obiektu polecenia.  
  
 [Icommandpropertiesimpl —](../../data/oledb/icommandpropertiesimpl-class.md)  
 Ta implementacja **ICommandProperties** interfejsu jest udostępniany przez funkcję statyczną zdefiniowane przez `BEGIN_PROPSET_MAP` makra. Obowiązkowe na polecenia.  
  
 [Icommandtextimpl —](../../data/oledb/icommandtextimpl-class.md)  
 Ustawia przechowuje i zwraca tekst polecenia. Obowiązkowe na polecenia.  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 Tworzy nowe polecenie z obiektu sesji i zwraca żądanego interfejsu na nowo utworzony polecenia. Opcjonalny interfejs dla obiektów sesji.  
  
 Klasy inne polecenia są `IColumnsInfoImpl` i `IAccessorImpl`, które zostały opisane w powyższej sekcji klasy zestawów wierszy.  
  
## <a name="data-source-classes"></a>Klasy źródła danych  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 Tworzy i usuwa połączenie z klienta. Obowiązkowego interfejsu na obiekty źródła danych i opcjonalnie interfejs moduły wyliczające.  
  
 [Idbpropertiesimpl —](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` jest obowiązkowego interfejsu dla obiekty źródła danych i opcjonalny interfejs dla wyliczenia. Jednak jeśli udostępnia moduł wyliczający **IDBInitialize**, musi on ujawniać `IDBProperties` (właściwości źródła danych).  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 Uzyskuje wskaźnik interfejsu do obiektu źródła danych. Obowiązkowego interfejsu w tej sesji.  
  
## <a name="other-classes"></a>Inne klasy  
 [Cutlprops —](../../data/oledb/cutlprops-class.md)  
 Implementuje właściwości dla różnych interfejsy właściwości OLE DB (na przykład `IDBProperties`, **ISessionProperties**, i `IRowsetInfo`).  
  
 [Ierrorrecordsimpl —](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 Implementuje OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) interfejsu, dodawanie rekordów i pobieranie rekordów z elementem członkowskim danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Szablony OLE DB](../../data/oledb/ole-db-templates.md)