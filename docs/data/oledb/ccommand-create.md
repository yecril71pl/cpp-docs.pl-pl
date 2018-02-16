---
title: CCommand::Create | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e84809d24479d85b01441c67b467102936b7f1aa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ccommandcreate"></a>CCommand::Create
Wywołania [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) można utworzyć polecenia dla określonej sesji, następnie wywołuje [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) na określanie tekstu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CCommandBase::Create(const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  


HRESULT CCommandBase::Create(const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  
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
 [CCommand, klasa](../../data/oledb/ccommand-class.md)