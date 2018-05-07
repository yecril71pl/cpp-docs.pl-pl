---
title: DEFINE_COMMAND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51f975b0477d29fbb35880c796f52612456c32c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="definecommand"></a>DEFINE_COMMAND
Określa polecenie, które będzie służyć do tworzenia zestawu wierszy, używając [CCommand](../../data/oledb/ccommand-class.md) klasy. Akceptuje tylko typy string odpowiadał typowi określonej aplikacji (ANSI lub Unicode).  
  
> [!NOTE]
>  Zaleca się, że używasz [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast `DEFINE_COMMAND`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
DEFINE_COMMAND(x, szCommand)  
  
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