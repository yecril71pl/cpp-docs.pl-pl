---
title: DEFINE_COMMAND | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEFINE_COMMAND
dev_langs: C++
helpviewer_keywords: DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cd2acfee6bb0f28acc774774e446e9efd4a5637b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="definecommand"></a>DEFINE_COMMAND
Określa polecenie, które będzie służyć do tworzenia zestawu wierszy, używając [CCommand](../../data/oledb/ccommand-class.md) klasy. Akceptuje tylko typy string odpowiadał typowi określonej aplikacji (ANSI lub Unicode).  
  
> [!NOTE]
>  Zaleca się, że używasz [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast `DEFINE_COMMAND`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
DEFINE_COMMAND(  
x  
,   
szCommand  
 )  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa klasy rekordu (polecenie) użytkownika.  
  
 `szCommand`  
 [in] Ciąg polecenia, które będą służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Uwagi  
 Ciąg polecenia, które określisz będzie służyć jako domyślny, jeśli nie określisz tekst polecenia w [CCommand::Open](../../data/oledb/ccommand-open.md) metody.  
  
 To makro akceptuje ciągów ANSI, jeśli skompilować aplikację jako ANSI lub ciągów Unicode w przypadku tworzenia aplikacji jako Unicode. Zaleca się, że używasz [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast `DEFINE_COMMAND`, ponieważ była akceptuje ciągów Unicode, niezależnie od typu aplikacji ANSI lub Unicode.  
  
## <a name="example"></a>Przykład  
 Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)