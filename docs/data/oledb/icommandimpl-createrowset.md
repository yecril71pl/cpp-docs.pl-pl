---
title: ICommandImpl::CreateRowset | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 45fcb53c6412f91c35ea26a5e7a732f5de2d3fcc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="icommandimplcreaterowset"></a>ICommandImpl::CreateRowset
Wywoływane przez [Execute](../../data/oledb/icommandimpl-execute.md) można utworzyć jeden zestaw wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      template template <class RowsetClass  
      >  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Parametry  
 `RowsetClass`  
 Szablon elementu członkowskiego klasy reprezentujący użytkownika klasy zestawu wierszy. Zwykle generowane przez kreatora.  
  
 `pUnkOuter`  
 [in] Wskaźnik do kontrolowania **IUnknown** interfejsu Jeśli zestawu wierszy jest tworzony jako część agregacji; w przeciwnym razie ma wartość null.  
  
 `riid`  
 [in] Odpowiada `riid` w `ICommand::Execute`.  
  
 `pParams`  
 [We/Wy] Odpowiada `pParams` w `ICommand::Execute`.  
  
 `pcRowsAffected`  
 Odpowiada `pcRowsAffected` w `ICommand::Execute`.  
  
 `ppRowset`  
 [We/Wy] Odpowiada `ppRowset` w `ICommand::Execute`.  
  
 `pRowsetObj`  
 [out] Wskaźnik do obiektu zestawu wierszy. Zazwyczaj ten parametr nie jest używany, ale można używać, jeśli w zestawie wierszy przed przekazaniem go do obiektu COM należy wykonać więcej pracy. Okres istnienia `pRowsetObj` jest powiązany `ppRowset`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość. Zobacz `ICommand::Execute` listę typowe wartości.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć więcej niż jeden zestaw wierszy lub podaj warunki do tworzenia różnych zestawów wierszy, wywołania różnych `CreateRowset` z poziomu **Execute**.  
  
 Zobacz [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) w *OLE DB Podręcznik programisty.*  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [ICommandImpl, klasa](../../data/oledb/icommandimpl-class.md)