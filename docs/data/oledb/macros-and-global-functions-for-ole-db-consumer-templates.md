---
title: Makra i funkcje globalne dla szablonów konsumentów OLE DB | Dokumentacja firmy Microsoft
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
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 57f61dd54855a2cf0196c0e269eda92295c818b9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra i funkcje globalne dla szablonów konsumentów OLE DB
Szablony OLE DB klienta obejmują następujące makra i funkcje globalne:  
  
### <a name="global-functions"></a>Globalne funkcje  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|Zrzuty danych OLE DB Błąd rekordu do urządzenia zrzutu, jeśli zostanie zwrócony błąd.|  
  
### <a name="accessor-map-macros"></a>Makra mapy metody dostępu  
  
|||  
|-|-|  
|[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)|Oznacza początek wpis dostępu.|  
|[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)|Oznacza początek wpisów map metody dostępu.|  
|[END_ACCESSOR](../../data/oledb/end-accessor.md)|Oznacza koniec wpis dostępu.|  
|[END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)|Oznacza koniec wpisów map metody dostępu.|  
  
### <a name="column-map-macros"></a>Makra mapy kolumny  
  
|||  
|-|-|  
|[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)|Oznacza początek wpisów map kolumny w klasie rekordu użytkownika.|  
|[BLOB_ENTRY](../../data/oledb/blob-entry.md)|Używany do wiązania dużego obiektu binarnego (BLOB).|  
|[BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)|Raporty długość kolumny danych obiektów BLOB.|  
|[BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)|Raporty długość i stan kolumny danych obiektów BLOB.|  
|[BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)|Informuje o stanie kolumny danych obiektów BLOB.|  
|[BLOB_NAME](../../data/oledb/blob-name.md)|Używany do wiązania dużego obiektu binarnego według nazwy kolumny.|  
|[BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)|Raporty długość kolumny danych obiektów BLOB.|  
|[BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)|Raporty długość i stan kolumny danych obiektów BLOB.|  
|[BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)|Informuje o stanie kolumny danych obiektów BLOB.|  
|[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)|Reprezentuje wpisem zakładek w zestawie wierszy. Wpis zakładki jest specjalnym rodzajem wpis w kolumnie.|  
|[COLUMN_ENTRY](../../data/oledb/column-entry.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych.|  
|[COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje `type`, *długość*, *dokładności*, `scale`, i *stan* parametrów.|  
|[COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje *długość* zmiennej.|  
|[COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje *stan* i *długość* parametrów.|  
|[COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje *dokładności* i `scale` parametrów.|  
|[COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje *długość* zmiennej *dokładności* i `scale` parametrów.|  
|[COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje *stan* i *długość* zmiennych, *dokładności* i `scale` parametrów.|  
|[COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje *stan* zmiennej *dokładności* i `scale` parametrów.|  
|[COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje *stan* zmiennej.|  
|[COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje `type` parametru.|  
|[COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych. Obsługuje `type` i `size` parametrów.|  
|[COLUMN_NAME](../../data/oledb/column-name.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy.|  
|[COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację — typ danych, rozmiar, precyzja, skala, długość kolumny i kolumny Stan.|  
|[COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację długość kolumny.|  
|[COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację długość kolumny i stanu.|  
|[COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację precyzję i skalę.|  
|[COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację długość precyzja, skala i kolumny.|  
|[COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację precyzja, skala długość kolumny i kolumny Stan.|  
|[COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację precyzja, skala i kolumnę stanu.|  
|[COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację kolumny stanu.|  
|[COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikacji typu danych.|  
|[COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikacji typu danych, precyzja i Skala.|  
|[COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikacji typu danych oraz rozmiar.|  
|[COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)|Reprezentuje powiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikacji typu i kolumny Stan danych.|  
|[END_COLUMN_MAP](../../data/oledb/end-column-map.md)|Oznacza koniec wpisów map kolumny.|  
  
### <a name="command-macros"></a>Makra poleceń  
  
|||  
|-|-|  
|[DEFINE_COMMAND](../../data/oledb/define-command.md)|Określa polecenie, które będzie służyć do tworzenia zestawu wierszy, używając [CCommand](../../data/oledb/ccommand-class.md) klasy. Akceptuje tylko typy string odpowiadał typowi określonej aplikacji (ANSI lub Unicode). Zaleca się, że używasz [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast `DEFINE_COMMAND`.|  
|[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)|Określa polecenie, które będzie służyć do tworzenia zestawu wierszy, używając [CCommand](../../data/oledb/ccommand-class.md) klasy. Obsługuje aplikacje, ANSI i Unicode.|  
  
### <a name="parameter-map-macros"></a>Makra mapy parametru  
  
|||  
|-|-|  
|[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)|Oznacza początek wpisów map parametru w klasie rekordu użytkownika.|  
|[END_PARAM_MAP](../../data/oledb/end-param-map.md)|Oznacza koniec wpisów map parametru.|  
|[SET_PARAM_TYPE](../../data/oledb/set-param-type.md)|Określa `COLUMN_ENTRY` makra, które należy wykonać `SET_PARAM_TYPE` makro jako danych wejściowych, wyjściowych lub wejścia/wyjścia.|  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)