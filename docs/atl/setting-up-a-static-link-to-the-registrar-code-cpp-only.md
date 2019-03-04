---
title: Konfigurowanie statycznego Linku do kodu rejestratora (tylko C++)
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: b95bd17abca3237710956f3a1bf1b1d6fa9df51e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265330"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Konfigurowanie statycznego Linku do kodu rejestratora (tylko C++)

C++ klienci mogą tworzyć statycznego linku do kodu rejestratora. Łączenie statyczne analizatora rejestratora dodaje około 5K do kompilacji wydania.

Najprostszym sposobem skonfigurowania łączenia statycznego zakłada określono [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) w deklaracji obiektu. (Jest to specyfikacja domyślne używane przez ATL.)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Aby utworzyć łącze statycznych przy użyciu DECLARE_REGISTRY_RESOURCEID

1. Określ [/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_STATYCZNE\_rejestru** zamiast **/D \_ATL\_DLL**.

1. Skompiluj ponownie.

## <a name="see-also"></a>Zobacz także

[Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)
