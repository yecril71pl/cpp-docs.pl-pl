---
title: "FtmBase::CreateGlobalInterfaceTable — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable
dev_langs: C++
helpviewer_keywords: CreateGlobalInterfaceTable method
ms.assetid: bb82a0c5-22b9-4844-9204-7922033d8b07
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d206e581166fb2bd685e6d4755d56e6d189656c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ftmbasecreateglobalinterfacetable-method"></a>FtmBase::CreateGlobalInterfaceTable — Metoda
Tworzy tabelę interfejsu globalnego (GIT).  
  
## <a name="syntax"></a>Składnia  
  
```  
static HRESULT CreateGlobalInterfaceTable(  
   __out IGlobalInterfaceTable **git  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `git`  
 Po tej operacji zakończeniu wskaźnik do Tabela interfejsu globalnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji zobacz temat "IGlobalInterfaceTable" w podrzędny "Interfejsy COM" w temacie "Odwołania COM" w bibliotece MSDN.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Ftmbase — klasa](../windows/ftmbase-class.md)