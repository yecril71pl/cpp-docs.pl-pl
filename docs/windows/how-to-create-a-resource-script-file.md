---
title: 'Porady: Tworzenie pliku skryptu zasobów (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 092cb7c33aab2805ca40410cac404d43ba5c9274
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313250"
---
# <a name="how-to-create-a-resource-script-file-c"></a>Porady: Tworzenie pliku skryptu zasobów (C++)

> [!NOTE]
> **Edytor zasobów** nie jest dostępny w wersji Express.
>
> W tym materiale dotyczy aplikacje pulpitu Windows. Projekty w językach .NET, nie używaj plików skryptu zasobu. Zobacz [pliki zasobów](../windows/resource-files-visual-studio.md), aby uzyskać więcej informacji.

### <a name="to-create-a-new-resource-script-rc-file"></a>Aby utworzyć nowego pliku zasobu skryptu (.rc)

1. Umieść fokus na istniejący folder projektu w taki sposób, w **Eksploratora rozwiązań**, na przykład `MyProject`.

   > [!NOTE]
   > Nie należy mylić folderze projektu z folderu rozwiązania w **Eksploratora rozwiązań**. Jeśli fokus jest umieszczony na **rozwiązania** folderu, wyborów dokonanych w **Dodaj nowy element** okno dialogowe (w kroku 3) będą inne.

2. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

3. W **Dodaj nowy element** okno dialogowe, kliknij przycisk **Visual C++** kliknij folder **pliku zasobów (.rc)** w okienku po prawej stronie.

4. Podaj nazwę pliku skryptu zasobu w **nazwa** tekst pola, a następnie kliknij przycisk **Otwórz**.

Możesz teraz [tworzenie](../windows/how-to-create-a-resource.md) i dodawania nowych zasobów do pliku .rc.

> [!NOTE]
> Skrypt zasobu (plik .rc) można dodać tylko do istniejącego projektu, który jest ładowany do środowiska IDE programu Visual Studio. Nie można utworzyć autonomiczny plik .rc (po jednym spoza projektu). [Szablony zasobów](../windows/how-to-use-resource-templates.md) (.rct — pliki) można tworzyć w dowolnym momencie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)