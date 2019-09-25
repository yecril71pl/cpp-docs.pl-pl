---
title: 'Instrukcje: Korzystanie z zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: 8dbf18d24c0369507743c3c1da624838f9ab4703
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "69513824"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Instrukcje: Korzystanie z zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows

Po utworzeniu klasycznego projektu pulpitu systemu Windows w programie Visual Studio 2017 jest on domyślnie skonfigurowany do kompilowania z wersją zestawu SDK systemu Windows 10, który został zainstalowany podczas instalowania lub C++ ostatniej aktualizacji obciążenia pulpitu. Ta wersja Windows SDK jest zgodna z systemem Windows 7 lub nowszym. Aby uzyskać więcej informacji na temat określania konkretnych wersji systemu Windows [, zobacz Używanie nagłówków systemu Windows](/windows/win32/WinProg/using-the-windows-headers) .

Jeśli chcesz użyć wcześniejszej wersji zestawu SDK, możesz otworzyć **projekt | Właściwości** i wybierz spośród innych wersji zestawu SDK dostępnych na liście rozwijanej wersja Windows SDK.

Począwszy od programu Visual Studio 2015 i zestawu SDK systemu Windows 10, Biblioteka CRT została rozdzielona na dwie części: jeden (ucrtbase), który zawiera funkcje, które są dopuszczalne do użycia w aplikacjach uniwersalnych systemu Windows, i jeden, który zawiera wszystkie inne (vcruntime140). Ponieważ zestaw SDK systemu Windows 10 zawiera nowe funkcje, takie jak wiele funkcji C99, należy wykonać następujące kroki, aby użyć tych funkcji. Zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

### <a name="to-target-the-windows-10-sdk"></a>Aby określić zestaw SDK systemu Windows 10

1. Upewnij się, że zestaw SDK systemu Windows 10 jest zainstalowany. Zestaw SDK systemu Windows 10 jest instalowany w ramach **tworzenia aplikacji C++ klasycznych** . Wersja autonomiczna jest dostępna w [plikach do pobrania i narzędzia dla systemu Windows 10](https://developer.microsoft.com/windows/downloads).

2. Otwórz menu skrótów dla węzła projektu, a następnie wybierz pozycję **Przekieruj wersję zestawu SDK**.

   ![Przekieruj wersję zestawu SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   Zostanie wyświetlone okno dialogowe **Przegląd akcji rozwiązania** .

   ![Przegląd akcji rozwiązania](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. Z listy rozwijanej **wersja platformy docelowej** wybierz wersję zestawu SDK systemu Windows 10, który ma zostać docelowy. Wybierz przycisk OK, aby zastosować zmianę.

   Należy pamiętać, że 8,1 w tym kontekście odnosi się do wersji Windows SDK, która jest również wstecznie zgodna z systemami Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 i Windows Vista.

   Jeśli ten krok zakończy się pomyślnie, w oknie danych wyjściowych zostanie wyświetlony następujący tekst:

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. Otwórz właściwości projektu i w sekcji **Właściwości konfiguracji** , zwróć uwagę na wartości **wersji platformy docelowej systemu Windows**. Zmiana wartości w tym miejscu ma taki sam skutek jak w przypadku tej procedury. Zobacz [Ogólne strony właściwości (projekt)](../build/reference/general-property-page-project.md).

   ![Wersja platformy docelowej](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Ta akcja zmienia wartości makr projektu, które zawierają ścieżki do plików nagłówkowych i plików bibliotek. Aby zobaczyć, co zostało zmienione, w sekcji **katalogi wizualizacji C++**  okna dialogowego **właściwości projektu** wybierz jedną z właściwości, takich jak **katalogi dołączania**, wybierz pozycję Otwórz listę rozwijaną, a \<następnie wybierz pozycję Edytuj >. Zostanie wyświetlone okno dialogowe **dołączanie katalogów** .

   ![Okno dialogowe dołączania katalogów](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Wybierz przycisk **makra > >** , a następnie przewiń w dół listę makr do Windows SDK makra, aby wyświetlić wszystkie nowe wartości.

   ![Makra Windows SDK](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. Powtórz w razie potrzeby inne projekty i Skompiluj ponownie rozwiązanie.

### <a name="to-target-the-windows-81-sdk"></a>Aby określić zestaw SDK Windows 8.1

1. Otwórz menu skrótów dla węzła projektu, a następnie wybierz pozycję **Przekieruj wersję zestawu SDK**.

2. Z listy rozwijanej **wersja platformy docelowej** wybierz pozycję **8,1**.

## <a name="see-also"></a>Zobacz także

[Aplikacje klasyczne systemu Windows ( C++wizualizacja)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)