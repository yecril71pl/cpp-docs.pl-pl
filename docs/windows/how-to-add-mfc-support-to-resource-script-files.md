---
title: 'Porady: Dodawanie obsługi MFC do plików skryptu zasobu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.add.MFC
dev_langs:
- C++
helpviewer_keywords:
- rc files, adding MFC support
- .rc files, adding MFC support
- MFC, adding support to resource scripts files
- resource script files, adding MFC support
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 194f2b4f2e6659412c9c2b5f688e0b73eea3bba5
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692031"
---
# <a name="how-to-add-mfc-support-to-resource-script-files"></a>Porady: dodawanie obsługi MFC do plików skryptu zasobu

Zwykle podczas kompilowania aplikacji MFC dla Windows przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), Kreator generuje zestaw podstawowych plików (w tym pliku zasobu skryptu (.rc)), który zawiera podstawowe funkcje programu Microsoft Foundation klasy (MFC). Jednak jeśli edytujesz plik .rc dla aplikacji Windows, która nie jest oparty na bibliotece MFC, następujące funkcje specyficzne dla platformy MFC nie są dostępne:

- Kreatorzy kodu MFC

- Ciągi menu podpowiedzi

- Zawartość list dla formantów pola kombi

- Obsługa formantu ActiveX

Można jednak dodać obsługę MFC do istniejących plików .rc, które nie mają.

### <a name="to-add-mfc-support-to-rc-files"></a>Aby dodać obsługę MFC do plików .rc

1. Otwórz pliku skryptu zasobu.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W [widok zasobów](../windows/resource-view-window.md), wyróżnij folder zasobów (na przykład MFC.rc).

3. W [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **tryb MFC** właściwości **True**.

   > [!NOTE]
   > Oprócz ustawienia tej flagi, plik .rc musi być częścią projektu MFC. Na przykład, ustawienie tylko **tryb MFC** do **True** w pliku .rc w systemie Win32 projektu nie daje żadnych funkcji MFC.

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)