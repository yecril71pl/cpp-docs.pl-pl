---
title: CRowset::FindNextRow | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset.FindNextRow
- CRowset<TAccessor>.FindNextRow
- ATL::CRowset::FindNextRow
- CRowset::FindNextRow
- CRowset<TAccessor>::FindNextRow
- CRowset.FindNextRow
- ATL.CRowset<TAccessor>.FindNextRow
- ATL::CRowset<TAccessor>::FindNextRow
- FindNextRow
dev_langs:
- C++
helpviewer_keywords:
- FindNextRow method
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4afc1db20970102ecddb9031f4f1b7a8f6906cf4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098228"
---
# <a name="crowsetfindnextrow"></a>CRowset::FindNextRow
Wyszukuje następny zgodny wiersz po zakładką.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT FindNextRow(DBCOMPAREOP op,   
  BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `op`  
 [in] Działanie do używania przy porównywaniu wartości wierszy. Dla wartości, zobacz [IRowsetFind::FindNextRow](https://msdn.microsoft.com/en-us/library/ms723091.aspx).  
  
 `pData`  
 [in] Wskaźnik do wartości do dopasowania.  
  
 `wType`  
 [in] Wskazuje typ danych wartości części buforu. Informacje wskaźników typu, zobacz [typy danych](https://msdn.microsoft.com/en-us/library/ms723969.aspx) w *OLE DB Podręcznik programisty* w zestawie Windows SDK.  
  
 `nLength`  
 [in] Długość, w bajtach konsumenta struktury danych przydzielone do wartości danych. Aby uzyskać więcej informacji, zobacz opis **cbMaxLen** w [struktury DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) w *OLE DB Podręcznik programisty.*  
  
 `bPrecision`  
 [in] Maksymalna dokładność używany podczas pobierania danych. Używana tylko wtedy, gdy `wType` jest `DBTYPE_NUMERIC`. Aby uzyskać więcej informacji, zobacz [konwersje DBTYPE_NUMERIC lub DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) w *OLE DB Podręcznik programisty*.  
  
 `bScale`  
 [in] Skalę używaną podczas pobierania danych. Używana tylko wtedy, gdy `wType` jest `DBTYPE_NUMERIC` lub **DBTYPE_DECIMAL**. Aby uzyskać więcej informacji, zobacz [konwersje DBTYPE_NUMERIC lub DBTYPE_DECIMAL](https://msdn.microsoft.com/en-us/library/ms719714.aspx) w *OLE DB Podręcznik programisty*.  
  
 *bSkipCurrent*  
 [in] Liczba wierszy z zakładki, w którym należy rozpocząć wyszukiwanie.  
  
 `pBookmark`  
 [in] Zakładki dla pozycji w poziomie której odbywa się rozpocząć wyszukiwanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymaga opcjonalny interfejs **IRowsetFind**, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetFind** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
 Aby dowiedzieć się, jak korzystanie z zakładek użytkowników, zobacz [przy użyciu zakładki](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowset — klasa](../../data/oledb/crowset-class.md)   
 [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx)