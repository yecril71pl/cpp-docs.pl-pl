---
title: Wstępnie zdefiniowane identyfikatory symboli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee34744a110b31eba125e4b6cbef48207081f5d7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578643"
---
# <a name="predefined-symbol-ids"></a>Wstępnie zdefiniowane symbole identyfikatorów

Po rozpoczęciu nowego projektu, w zależności od typu projektu niektóre symbole identyfikatorów są wstępnie zdefiniowane do użycia. Te identyfikatory symboli obsługuje różnych bibliotek i typów projektów, takie jak MFC. Reprezentują one typowych zadań, które zwykle znajdują się w dowolnej aplikacji lub akcje elementów sprzętu, takich jak drukarka lub myszy.

Te identyfikatory symboli nabierają znaczenia podczas pracy z zasobami. Są one dostępne, gdy edytowanie tabel akceleratora. Niektóre z nich są już skojarzone z klawisze wirtualne. Są one również dostępne za pośrednictwem [okno właściwości](/visualstudio/ide/reference/properties-window). Można przypisać dowolny wstępnie zdefiniowane symbole identyfikatorów nowe zasoby, lub można przypisać klawisze skrótów do nich i funkcje związane z symbolem, który identyfikator automatycznie kojarzy z tej kombinacji klawiszy.

Te biblioteki ma wstępnie zdefiniowane symbole, które będą wyświetlane jako część projektu:

- [Wstępnie zdefiniowane symbole MFC](../windows/mfc-predefined-symbols.md)

- [Wstępnie zdefiniowane symbole ATL](../windows/atl-predefined-symbols.md)

- [Wstępnie zdefiniowane symbole Win32](../windows/win32-predefined-symbols.md)

   > [!NOTE]
   > Wstępnie zdefiniowane symbole są zawsze tylko do odczytu.

## <a name="requirements"></a>Wymagania

Win32, ATL i MFC

## <a name="see-also"></a>Zobacz też

[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)