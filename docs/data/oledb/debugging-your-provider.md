---
title: Debugowanie dostawcy
ms.date: 10/29/2018
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: f80ce5dc82dd2baeefe3410a488a5fefda0e9bf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211097"
---
# <a name="debugging-your-provider"></a>Debugowanie dostawcy

Istnieją dwa sposoby debugowania dostawcy:

- Ze względu na to, że dostawcy są tworzone w procesie, można utworzyć pewien kod konsumenta przy użyciu szablonów konsumentów OLE DB i przekroczyć dostawcę w normalny sposób.

- Możesz użyć różnych narzędzi dostarczanych z wizualizacją C++.

## <a name="to-use-debugging"></a>Aby używać debugowania

1. Otwórz projekt dostawcy.

1. W menu **projekty** kliknij polecenie **Właściwości**.

1. W oknie dialogowym **strony właściwości** kliknij kartę **debugowanie** .

1. Wybierz odpowiednie opcje, a następnie kliknij przycisk **OK**.

1. Ustaw punkty przerwania, a następnie Debuguj w zwykły sposób.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
