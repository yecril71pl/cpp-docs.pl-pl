---
title: CCommand::Create | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs: C++
helpviewer_keywords: Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 425e86008b97defe50e2c47e099b3b21c900bc1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandcreate"></a>CCommand::Create
Wywołania [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) można utworzyć polecenia dla określonej sesji, następnie wywołuje [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) na określanie tekstu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `session`  
 [in] Sesję, na którym chcesz utworzyć polecenie.  
  
 `wszCommand`  
 [in] Wskaźnik do tekst Unicode ciąg polecenia.  
  
 `szCommand`  
 [in] Wskaźnik do tekstu ANSI ciąg polecenia.  
  
 `guidCommand`  
 [in] Identyfikator GUID, który określa składnię i reguły ogólne dla dostawcy do użycia podczas analizowania tekstu polecenia. Aby uzyskać opis dialekty, zobacz [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy formę **Utwórz** polecenia ciąg znaków Unicode. Drugiej formy **Utwórz** przyjmuje ciąg polecenia ANSI (udostępnionymi w celu zapewnienia zgodności z istniejącymi aplikacjami ANSI).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CCommand — klasa](../../data/oledb/ccommand-class.md)