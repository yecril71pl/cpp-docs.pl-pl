---
title: Klasa CCommand | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
dev_langs:
- C++
helpviewer_keywords:
- CCommand class
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5ec786bff30745a986ecc643cd42f0d8975b0ccf
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ccommand-class"></a>Klasa CCommand
Udostępnia metody do ustawiania i wykonywania polecenia.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CNoAccessor,  
          template <typename T> class TRowset = CRowset,  
          class TMultiple = CNoMultipleResults>  
class CCommand :   
           public CAccessorRowset <TAccessor, TRowset>,  
           public CCommandBase,  
           public TMultiple  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Typ klasy metody dostępu (takich jak `CDynamicParameterAccessor`, `CDynamicStringAccessor`, lub `CEnumeratorAccessor`) oznaczający polecenie ma korzystać. Wartość domyślna to `CNoAccessor`, która określa, że klasa nie obsługuje parametrów lub kolumny wyjściowe.  
  
 `TRowset`  
 Typ klasy zestawu wierszy (takich jak `CArrayRowset` lub `CNoRowset`) oznaczający polecenie ma korzystać. Wartość domyślna to `CRowset`.  
  
 `TMultiple`  
 Polecenia OLE DB mogą zwracać wiele wyników, określ [cmultipleresults —](../../data/oledb/cmultipleresults-class.md). W przeciwnym razie użyj [cnomultipleresults —](../../data/oledb/cnomultipleresults-class.md). Aby uzyskać więcej informacji, zobacz [interfejsu IMultipleResults](https://msdn.microsoft.com/en-us/library/ms721289.aspx).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zamknij](../../data/oledb/ccommand-close.md)|Zamyka bieżące polecenie.|  
|[GetNextResult](../../data/oledb/ccommand-getnextresult.md)|Pobiera następnego wyniku, gdy zestawów za pomocą wielu wyników.|  
|[Otwórz](../../data/oledb/ccommand-open.md)|Wykonuje i opcjonalnie powiązanie polecenia.|  
  
### <a name="inherited-methods"></a>Dziedziczonej metody  
  
|||  
|-|-|  
|[Utwórz](../../data/oledb/ccommand-create.md)|Tworzy nowe polecenie dla określonej sesji, a następnie ustawia tekst polecenia.|  
|[CreateCommand](../../data/oledb/ccommand-createcommand.md)|Tworzy nowe polecenie.|  
|[GetParameterInfo](../../data/oledb/ccommand-getparameterinfo.md)|Pobiera listę parametrów polecenia, ich nazwy i typy.|  
|[Przygotowanie](../../data/oledb/ccommand-prepare.md)|Weryfikuje i optymalizuje bieżącego polecenia.|  
|[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)|Zwalnia akcesor parametru, jeśli to konieczne, a następnie zwalnia polecenia.|  
|[SetParameterInfo](../../data/oledb/ccommand-setparameterinfo.md)|Określa typ macierzysty każdego parametru polecenia.|  
|[Unprepare](../../data/oledb/ccommand-unprepare.md)|Odrzuca bieżący plan wykonania polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa jest używana, gdy trzeba wykonać operację na podstawie parametru lub wykonania polecenia. Jeśli potrzebujesz tylko otworzyć prosty zestaw wierszy, użyj [CTable](../../data/oledb/ctable-class.md) zamiast tego.  
  
 Klasa akcesor używanego określa metodę wiązania parametrów i danych.  
  
 Należy pamiętać, że nie możesz użyć procedur składowanych z dostawcy OLE DB dla Jet ponieważ ten dostawca nie obsługuje przechowywanych procedur (tylko stałe są dozwolone w ciągach kwerendy).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)