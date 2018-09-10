---
title: Zmiana symbolu lub nazwy symbolu (ID) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols [C++], names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b80c854d144f0f2010d1482a03f692062ea81ef
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315902"
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>Zmiana symbolu lub nazwy symbolu (ID)

Podczas tworzenia nowego zasobu lub obiektu zasobu, środowisko programistyczne przypisuje mu nazwę symbolu domyślną, na przykład IDD_DIALOG1. Możesz użyć [okno właściwości](/visualstudio/ide/reference/properties-window) zmienić domyślną nazwę symbolu lub zmień nazwę symbolu już skojarzony z zasobem.

### <a name="to-change-a-resources-symbol-name"></a>Aby zmienić nazwę symbolu zasobu

1. W [widok zasobów](../windows/resource-view-window.md), wybierz zasób.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W **właściwości** okna, wpisz nową nazwę symbolu lub wybierz z listy istniejących symboli w **identyfikator** pole.

   Jeśli wpiszesz nową nazwę symbolu, jest automatycznie przypisywany wartość.

Możesz użyć [okno dialogowe symboli zasobów](../windows/resource-symbols-dialog-box.md) się zmienić nazwy symboli nie jest aktualnie przypisany do zasobu. Aby uzyskać więcej informacji, zobacz [zmiana nieprzypisanych symboli](../windows/changing-unassigned-symbols.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md)  
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)