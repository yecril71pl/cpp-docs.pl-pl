---
title: ICommandTextImpl::SetCommandText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
dev_langs: C++
helpviewer_keywords: SetCommandText method
ms.assetid: 7271bfb0-7a8b-4281-b3e8-7c80b9fe79d4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d96051d4a990a998aed9e70a4d93a2a7fb4dfe11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="icommandtextimplsetcommandtext"></a>ICommandTextImpl::SetCommandText
Ustawia tekst polecenia, zastępując istniejący tekst polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD(SetCommandText)(   
   REFGUID rguidDialect,   
   LPCOLESTR pwszCommand    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Icommandtextimpl — klasa](../../data/oledb/icommandtextimpl-class.md)   
 [ICommandTextImpl::GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)