---
title: IRowsetNotifyCP::Fire_OnRowsetChange | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
dev_langs: C++
helpviewer_keywords: Fire_OnRowsetChange method
ms.assetid: 412a9ec2-5041-4c56-acda-dc8f8e9b35f3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a59f8e13a371472e8355f9fd6903ada04c09d6c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetnotifycpfireonrowsetchange"></a>IRowsetNotifyCP::Fire_OnRowsetChange
Emituje [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) zdarzenia do wszystkich obiektów nasłuchujących w punkcie połączenia **IID_IRowsetNotify** powiadomił użytkowników zmian wpływających na cały zestaw wierszy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT Fire_OnRowsetChange(  
   IRowset* pRowset,  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Irowsetnotifycp — klasa](../../data/oledb/irowsetnotifycp-class.md)