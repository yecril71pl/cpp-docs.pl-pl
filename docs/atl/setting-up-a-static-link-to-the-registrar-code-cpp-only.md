---
title: Konfigurowanie statycznego linku do kodu rejestratora (tylko C++)
description: Jak statycznie łączyć kod języka C++ z kodem rejestratora ATL.
ms.date: 09/03/2020
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: f08f7d9433ae1344c7a98a5c52502d03bad21e91
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609157"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Konfigurowanie statycznego linku do kodu rejestratora (tylko C++)

Klienci języka C++ mogą utworzyć statyczny link do kodu rejestratora. Statyczne łączenie analizatora rejestratora dodaje około 5 K do kompilacji wydania.

Najprostszym sposobem skonfigurowania konsolidacji statycznej jest założenie, że określono [`DECLARE_REGISTRY_RESOURCEID`](reference/registry-macros.md#declare_registry_resourceid) w deklaracji obiektu. (Jest to domyślna Specyfikacja używana przez ATL).

## <a name="to-create-a-static-link-using-declare_registry_resourceid"></a>Aby utworzyć łącze statyczne przy użyciu `DECLARE_REGISTRY_RESOURCEID`

1. Określ **`/D _ATL_STATIC_REGISTRY`** zamiast **`/D _ATL_DLL`** w wierszu polecenia CL. Aby uzyskać więcej informacji, zobacz [`/D`](../build/reference/d-preprocessor-definitions.md).

1. Skompiluj ponownie.

## <a name="see-also"></a>Zobacz też

[Składnik rejestru (Rejestrator)](../atl/atl-registry-component-registrar.md)
