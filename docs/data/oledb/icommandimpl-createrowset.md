---
title: ICommandImpl::CreateRowset | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateRowset method
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6909f8f6825aacf55c000bfd87e0282365180559
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100645"
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