---
title: "Porady: używanie systemu Windows 10 SDK w aplikacji pulpitu systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f5e6f09b371c4d295b4bcdff469396a2671d22a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Porady: używanie systemu Windows 10 SDK w aplikacji pulpitu systemu Windows
Po utworzeniu klasycznego projekt pulpitu systemu Windows w programie Visual Studio 2017 ją skonfigurowano domyślnie do kompilacji z wersją systemu Windows 10 SDK został zainstalowany, gdy obciążenie pulpitu C++ został zainstalowany lub ostatniej aktualizacji. Ta wersja zestawu Windows SDK jest zgodna z wszystkich najnowszych wersji systemu Windows. Jeśli chcesz przeanalizować starszej wersji zestawu SDK, można otworzyć projektu | Właściwości i wybierz jedną z dostępnych na liście rozwijanej zestawu SDK systemu Windows w wersji wersji zestawu SDK.  
  
 Począwszy od programu Visual Studio 2015 i zestawu Windows 10 SDK, biblioteka CRT został podzielony na dwie części jednego (ucrtbase) zawiera funkcje, które są dozwolone do użycia w aplikacji uniwersalnych systemu Windows, a drugi zawierający wszystkie inne elementy (vcruntime140). Ponieważ zestaw Windows 10 SDK zawiera nowe funkcje, takie jak wiele funkcji C99, należy wykonać następujące kroki, aby można było używać tych funkcji. Zobacz [funkcje bibliotek CRT](../c-runtime-library/crt-library-features.md).  
  
### <a name="to-target-the-windows-10-sdk"></a>Docelowy zestaw Windows 10 SDK  
  
1.  Upewnij się, że jest zainstalowany zestaw Windows 10 SDK. Zestaw Windows 10 SDK jest instalowane jako część [narzędzi dla systemu Windows 10](http://go.microsoft.com/fwlink/p/?linkid=617631).  
  
2.  Otwórz menu skrótów węzła projektu i wybierz polecenie **Przekieruj zestawu SDK w wersji**.  
  
     ![Przekieruj do zestawu SDK w wersji](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     **Przeglądu rozwiązania akcje** zostanie wyświetlone okno dialogowe.  
  
     ![Przejrzyj akcje rozwiązania](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  W **docelową wersję platformy** listy rozwijanej wybierz wersję docelową zestawu Windows 10 SDK. Wybierz przycisk OK, aby zastosować zmiany.  
  
     Należy pamiętać, że 8.1, w tym kontekście odwołuje się do wersji zestawu Windows SDK, który jest także wstecznie zgodne z systemem Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 i Windows Vista.  
  
     Jeśli ten krok zakończy się pomyślnie, zostanie wyświetlony następujący tekst w oknie danych wyjściowych:  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  Otwórz właściwości projektu, a następnie w **właściwości konfiguracji, ogólne** sekcji, zwróć uwagę na wartości z **docelową wersję platformy Windows**. Zmiana w tym miejscu wartość ma ten sam efekt co następującej procedury. Zobacz [ogólna strona właściwości (projekt)](../ide/general-property-page-project.md).  
  
     ![Docelowa wersja platformy](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     Ta akcja umożliwia zmianę wartości makra projektu, które ścieżki do plików nagłówka i pliki bibliotek dołączanych plików. Aby zobaczyć, co zmieniono w sekcji Visual C++ katalogów okna dialogowego właściwości projektu i wybierz jedną z właściwości, takie jak katalogi dołączenia, wybierz Otwórz listę rozwijaną, a następnie wybierz pozycję \<Edytuj >. **Katalogi dołączenia** zostanie wyświetlone okno dialogowe.  
  
     ![Obejmują katalogów — okno dialogowe](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     Wybierz **makra >>** przycisk, a następnie przewiń w dół listę makra makr zestawu Windows SDK, aby zobaczyć nowe wartości.  
  
     ![Makra zestawu SDK systemu Windows](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  W razie potrzeby powtórz dla innych projektów i ponownie skompiluj rozwiązanie.  
  
### <a name="to-target-the-windows-81-sdk"></a>Docelowy zestaw SDK Windows 8.1  
  
1.  Otwórz menu skrótów węzła projektu i wybierz polecenie **Przekieruj zestawu SDK w wersji**.  
  
2.  Na liście rozwijanej docelową wersję platformy wybierz 8.1.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje systemu Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)
