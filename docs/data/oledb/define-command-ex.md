---
title: DEFINE_COMMAND_EX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e3fb4ce434f578ed79f3ed086adf73a6a49da870
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
Określa polecenie, które będzie służyć do tworzenia zestawu wierszy, używając [CCommand](../../data/oledb/ccommand-class.md) klasy. Obsługuje aplikacje, Unicode i ANSI.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
DEFINE_COMMAND_EX(x, wszCommand)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa klasy rekordu (polecenie) użytkownika.  
  
 `wszCommand`  
 [in] Ciąg polecenia, które będą służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Uwagi  
 Ciąg polecenia, które określisz będzie służyć jako domyślny, jeśli nie określisz tekst polecenia w [CCommand::Open](../../data/oledb/ccommand-open.md) metody.  
  
 To makro akceptuje ciągów Unicode, niezależnie od typu aplikacji. To makro jest preferowana przez [DEFINE_COMMAND](../../data/oledb/define-command.md) ponieważ obsługuje on Unicode oraz aplikacje ANSI.  
  
## <a name="example"></a>Przykład  
 Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)