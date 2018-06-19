---
title: CRowset::Insert | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset<TAccessor>.Insert
- CRowset.Insert
- CRowset<TAccessor>.Insert
- CRowset<TAccessor>::Insert
- ATL::CRowset<TAccessor>::Insert
- ATL.CRowset.Insert
- CRowset::Insert
- ATL::CRowset::Insert
dev_langs:
- C++
helpviewer_keywords:
- Insert method
ms.assetid: 6a64a1c3-10ac-4296-8685-0fd6fe63a13b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 44dddd6f3da835744463a9a95c44aa224d29d626
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098449"
---
# <a name="crowsetinsert"></a>CRowset::Insert
Tworzy i inicjuje nowy wiersz przy użyciu danych z metody dostępu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Insert(int nAccessor = 0,   
   bool bGetHRow = false) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nAccessor`  
 [in] Liczba dostępu do użycia podczas wstawiania danych.  
  
 *bGetHRow*  
 [in] Wskazuje, czy są pobierane dojście wstawionego wiersza.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymaga opcjonalny interfejs `IRowsetChange`, który może nie być obsługiwany na wszystkich dostawców; Jeśli jest to możliwe, metoda zwraca **E_NOINTERFACE**. Należy także ustawić **DBPROP_IRowsetChange** do `VARIANT_TRUE` przed wywołaniem **Otwórz** tabeli lub polecenie zawierający zestaw wierszy.  
  
 Wstaw może zakończyć się niepowodzeniem, jeśli co najmniej jedna kolumna nie jest zapisywalny. Zmodyfikuj mapy kursora, aby rozwiązać ten problem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak na dostęp do źródła danych za pomocą zestawu wierszy, a następnie wstawianie ciągu przy użyciu tabeli w tym zestawie wierszy.  
  
 Najpierw Utwórz klasę tabeli, wstawiając nowy obiekt ATL do projektu. Na przykład, kliknij prawym przyciskiem myszy projekt w okienku obszaru roboczego i wybierz **nowy obiekt ATL**. Z **dostęp do danych** kategorii, wybierz opcję **konsumenta**. Tworzenie typu obiektu konsumenta **tabeli**. (Wybieranie **tabeli** tworzy zestawu wierszy bezpośrednio z tabeli; zaznaczanie **polecenia** tworzy wierszy za pomocą polecenia SQL.) Wybierz źródło danych, określając tabeli za pomocą którego można uzyskać dostępu do tego źródła danych. Wywołanie obiektu konsumenta **CCustomerTable**, następnie czy implementuje kodu wstawiania w następujący sposób:  
  
 [!code-cpp[NVC_OLEDB_Consumer#10](../../data/oledb/codesnippet/cpp/crowset-insert_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRowset, klasa](../../data/oledb/crowset-class.md)