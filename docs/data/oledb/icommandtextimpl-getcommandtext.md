---
title: ICommandTextImpl::GetCommandText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
dev_langs: C++
helpviewer_keywords: GetCommandText method
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b24afdf4bddd30ca2644edb1c7970a193251bdb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="icommandtextimplgetcommandtext"></a>ICommandTextImpl::GetCommandText
Zwraca tekst polecenia ustawione przez ostatnie wywołanie [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD(GetCommandText)(   
   GUID * pguidDialect,   
   LPOLESTR * ppwszCommand    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) w *OLE DB Podręcznik programisty*. *PguidDialect* parametru jest ignorowana przez domyślny.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [ICommandTextImpl, klasa](../../data/oledb/icommandtextimpl-class.md)