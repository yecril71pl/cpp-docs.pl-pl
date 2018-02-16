---
title: CCommand::Open | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1a58dc67735a4f236c79ff6c777a4510dfdfcd12
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ccommandopen"></a>CCommand::Open
Wykonuje i opcjonalnie powiązanie polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [in] Sesja, w którym można wykonać polecenia.  
  
 `wszCommand`  
 [in] Polecenie do wykonania, został przekazany jako ciąg Unicode. Może być **NULL** przy użyciu `CAccessor`, w takim przypadku polecenie zostanie pobrana wartość przekazana do [DEFINE_COMMAND](../../data/oledb/define-command.md) makra. Zobacz [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) w *OLE DB Podręcznik programisty* szczegółowe informacje.  
  
 `szCommand`  
 [in] Taki sam jak `wszCommand` z tą różnicą, że ten parametr przyjmuje ciąg polecenia ANSI. Czwarty formularza tej metody może zająć wartości NULL. W dalszej części tego tematu, aby uzyskać więcej informacji, zobacz "Uwagi".  
  
 *pPropSet*  
 [in] Wskaźnik do tablicy [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury zawierające właściwości i wartości, które można ustawić. Zobacz [zestawy właściwości i grup właściwości](https://msdn.microsoft.com/en-us/library/ms713696.aspx) w *OLE DB Podręcznik programisty* w systemie Windows SDK.  
  
 `pRowsAffected`  
 [We/Wy] Wskaźnik do pamięci, w której jest zwracana liczba wierszy, których to dotyczy, za pomocą polecenia. Jeśli  *\*pRowsAffected* jest **NULL**, zwracany jest nie liczba wierszy. W przeciwnym razie **Otwórz** ustawia *`pRowsAffected` zgodnie z następujących warunków:  
  
|IF|Następnie|  
|--------|----------|  
|**CParamSets** elementu `pParams` jest większa niż 1|*`pRowsAffected` reprezentuje całkowita liczba wierszy dotyczy wszystkich zestawów parametrów określony podczas wykonywania.|  
|Liczba wierszy, których dotyczy nie jest dostępna|*`pRowsAffected` ma ustawioną wartość -1.|  
|Polecenie nie aktualizowanie, usuwanie lub wstawić wierszy|*`pRowsAffected` nie jest zdefiniowana.|  
  
 `guidCommand`  
 [in] Identyfikator GUID, który określa składnię i reguły ogólne dla dostawcy do użycia podczas analizowania tekstu polecenia. Zobacz [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) i [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) w *OLE DB Podręcznik programisty* szczegółowe informacje.  
  
 `bBind`  
 [in] Określa, czy można powiązać polecenie automatycznie po wykonywana. Wartość domyślna to **true**, co powoduje, że polecenie może być powiązane automatycznie. Ustawienie `bBind` do **false** uniemożliwia automatyczne powiązania polecenie tak, aby można powiązać ręcznie. (Ręczne powiązanie jest znaczący użytkownikom OLAP).  
  
 `ulPropSets`  
 [in] Liczba [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) przekazano struktury *pPropSet* argumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Pierwsze trzy rodzaje **Otwórz** otrzymuje sesji, Utwórz polecenie i wykonaj polecenie powiązanie parametrów w razie potrzeby.  
  
 Pierwszy formę **Otwórz** polecenia ciąg znaków Unicode i nie ma wartości domyślnej.  
  
 Drugiej formy **Otwórz** ciąg polecenia ANSI i ma wartości domyślnej (udostępnionymi w celu zapewnienia zgodności z istniejącymi aplikacjami ANSI).  
  
 Trzeci formę **Otwórz** umożliwia ciąg polecenia na wartość NULL, ponieważ typ `int` z wartością domyślną wartością null. Dotyczy wywoływania `Open(session, NULL);` lub `Open(session);` , ponieważ wartość NULL jest typu `int`. Ta wersja wymaga i potwierdza, że `int` parametr mieć wartości NULL.  
  
 Użyj formy czwarty **Otwórz** gdy polecenia zostały już utworzone i chcesz wykonać jedną [Prepare](../../data/oledb/ccommand-prepare.md) i wykonania wielu.  
  
> [!NOTE]
>  **Otwórz** wywołania **Execute**, który z kolei wywołuje `GetNextResult`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CCommand, klasa](../../data/oledb/ccommand-class.md)