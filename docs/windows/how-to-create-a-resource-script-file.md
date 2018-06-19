---
title: 'Porady: Tworzenie pliku skryptu zasobu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files, creating
- .rc files, creating
- resource script files, creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a15352640a39ff6adc3b5a956a1f32c9fd414272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875526"
---
# <a name="how-to-create-a-resource-script-file"></a>Porady: tworzenie pliku skryptu zasobu
> [!NOTE]
>  Edytor zasobów nie jest dostępna w wersji Express.  
>   
>  W tym materiale ma zastosowanie do aplikacji klasycznych systemu Windows. Projekty w językach .NET należy używać pliki skryptów zasobów. Zobacz [pliki zasobów](../windows/resource-files-visual-studio.md), aby uzyskać więcej informacji.  
  
### <a name="to-create-a-new-resource-script-rc-file"></a>Aby utworzyć nowy plik skryptu (.rc) zasobu  
  
1.  Umieszczanie fokusu do istniejącego folderu projektu w `Solution Explorer`, na przykład "MyProject".  
  
    > [!NOTE]
    >  Nie należy mylić folderu projektu z folderu rozwiązania w Eksploratorze rozwiązań. Wprowadza fokusu w folderze rozwiązania wyborów dokonanych w **Dodaj nowy element** okno dialogowe (w kroku 3) będą inne.  
  
2.  Na **projektu** kliknij menu **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **Visual C++** a następnie wybierz folder **pliku zasobów (.rc)** w okienku po prawej stronie.  
  
4.  Podaj nazwę pliku skryptu zasobu w **nazwa** tekstu, a następnie kliknij przycisk **Otwórz**.  
  
 Możesz teraz [utworzyć](../windows/how-to-create-a-resource.md) i dodać nowe zasoby do pliku .rc.  
  
> [!NOTE]
>  Skrypt zasobu (plik .rc) można dodawać tylko do istniejącego projektu, który jest ładowany do środowiska IDE programu Visual Studio. Nie można utworzyć autonomiczny plik .rc (jeden poza projektem). [Szablony zasobów](../windows/how-to-use-resource-templates.md) (.rct — pliki) mogą być tworzone w dowolnym momencie.  
  
 RRequirements  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)