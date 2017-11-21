---
title: "Konfigurowanie statyczne łącze do kodu rejestratora (tylko C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b8eb77bc6f99ab6b7d8ca9d51f1a7a8549d8f0c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Konfigurowanie statyczne łącze do kodu rejestratora (tylko C++)
C++, klienci mogą tworzyć statyczne łącze do kodu rejestratora. Statyczne połączenie analizator rejestratora dodaje około 5K do kompilacji wydania.  
  
 Najprostszym sposobem skonfigurowania statycznego łączenia zakłada określono [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) w deklaracji z obiektu. (To jest specyfikacja domyślne używane przez ATL.)  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Aby utworzyć łącze statycznych przy użyciu DECLARE_REGISTRY_RESOURCEID  
  
1.  Określ [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` zamiast /D**_ATL_DLL**.  
  
2.  Skompiluj ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)

