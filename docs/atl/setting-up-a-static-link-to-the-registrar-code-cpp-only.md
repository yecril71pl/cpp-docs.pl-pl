---
title: Konfigurowanie statycznego Linku do kodu rejestratora (tylko C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a66ca33aa95ea6ffd59860cf0a55e51266ef5cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757701"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Konfigurowanie statycznego Linku do kodu rejestratora (tylko C++)

C++ klienci mogą tworzyć statycznego linku do kodu rejestratora. Łączenie statyczne analizatora rejestratora dodaje około 5K do kompilacji wydania.

Najprostszym sposobem skonfigurowania łączenia statycznego zakłada określono [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) w deklaracji obiektu. (Jest to specyfikacja domyślne używane przez ATL.)

### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Aby utworzyć łącze statycznych przy użyciu DECLARE_REGISTRY_RESOURCEID

1. Określ [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` zamiast /D **_ATL_DLL**.

2. Skompiluj ponownie.

## <a name="see-also"></a>Zobacz też

[Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)

