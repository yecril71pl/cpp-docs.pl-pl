---
title: DEFINE_COMMAND_EX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2a77fa0d6655edeee88df3c7c45e1936a766b40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101045"
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