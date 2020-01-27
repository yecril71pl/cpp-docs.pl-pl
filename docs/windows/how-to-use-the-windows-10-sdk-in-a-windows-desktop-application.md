---
title: 'Instrukcje: korzystanie z zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows'
description: Jak ustawić docelową wersję zestawu SDK w projekcie aplikacji klasycznych systemu Windows, aby użyć zestawu SDK systemu Windows 10.
ms.custom: get-started-article
ms.date: 01/22/2020
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: c1d71b591398453f7cee02aa22cd2e377991588f
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725737"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Instrukcje: korzystanie z zestawu SDK systemu Windows 10 w aplikacji klasycznej systemu Windows

Podczas tworzenia nowego projektu klasycznego systemu Windows w programie Visual Studio domyślnie przeznaczony jest zestaw SDK systemu Windows 10. Program Visual Studio instaluje wersję tego zestawu SDK podczas instalacji obciążeń C++ pulpitu. Zestaw SDK systemu Windows 10 obsługuje pisanie kodu dla systemu Windows 7 z dodatkiem SP1 i nowszych. Aby uzyskać więcej informacji na temat określania konkretnych wersji systemu Windows, zobacz [Używanie nagłówków systemu Windows](/windows/win32/WinProg/using-the-windows-headers) i [Aktualizowanie programu winver i _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

W przypadku uaktualniania istniejącego projektu można wybrać: można nadal używać Windows SDK docelowej określonych w projekcie. Możesz też przekierować projekt, aby użyć zestawu SDK systemu Windows 10. Zestaw SDK systemu Windows 10 zapewnia zalety obsługi najnowszych systemów operacyjnych i standardów językowych.

## <a name="use-the-right-windows-sdk-for-your-project"></a>Użyj odpowiednich Windows SDK dla projektu

Począwszy od programu Visual Studio 2015, biblioteka środowiska uruchomieniowego języka C (CRT) została rozdzielona na dwie części: jedna część, ucrtbase, zawiera standardowe i specyficzne dla firmy Microsoft funkcje CRT, których można używać w aplikacjach uniwersalnych systemu Windows. Ta biblioteka jest teraz znana jako uniwersalna CRT lub UCRT, która została przeniesiona do zestawu Windows 10 SDK. UCRT zawiera wiele nowych funkcji, takich jak funkcje C99, które są konieczne do obsługi najnowszych C++ standardów języka. Druga część oryginalnej CRT to vcruntime. Zawiera obsługę środowiska uruchomieniowego języka C, uruchamianie i kod zakończenia oraz wszystkie inne, które nie przechodzą do UCRT. Biblioteka vcruntime jest instalowana wraz z C++ kompilatorem i zestawem narzędzi w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

UCRT jest teraz składnikiem systemu zainstalowanym w każdej wersji systemu Windows 10. Jest on również dostępny jako składnik instalowalny dla wszystkich wcześniejszych obsługiwanych wersji systemu Windows. Zestawu SDK systemu Windows 10 można używać do obsługi wszystkich obsługiwanych wersji systemu Windows. Aby uzyskać pełną listę obsługiwanych systemów operacyjnych, zobacz [zestaw SDK systemu Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

Aby przekierować projekty do korzystania z zestawu SDK systemu Windows 10 podczas uaktualniania z wersji projektu przed programem Visual Studio 2015, wykonaj następujące kroki:

### <a name="to-target-the-windows-10-sdk"></a>Aby określić zestaw SDK systemu Windows 10

1. Upewnij się, że zestaw SDK systemu Windows 10 jest zainstalowany. Zestaw SDK systemu Windows 10 jest instalowany w ramach **tworzenia aplikacji C++ klasycznych** . Wersja autonomiczna jest dostępna w [plikach do pobrania i narzędzia dla systemu Windows 10](https://developer.microsoft.com/windows/downloads).

1. Otwórz menu skrótów dla węzła projektu, a następnie wybierz pozycję **Przekieruj projekty**. (We wcześniejszych wersjach programu Visual Studio wybierz pozycję **Przekieruj wersję zestawu SDK**). Zostanie wyświetlone okno dialogowe **Przegląd akcji rozwiązania** .

   ![Przegląd akcji rozwiązania](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

1. Z listy rozwijanej **wersja platformy docelowej** wybierz wersję zestawu SDK systemu Windows 10, który ma zostać docelowy. Ogólnie mówiąc, zalecamy wybranie najnowszej zainstalowanej wersji. Wybierz przycisk **OK** , aby zastosować zmianę.

   8,1 w tym kontekście odwołuje się do zestawu SDK Windows 8.1.

   Jeśli ten krok zakończy się pomyślnie, w oknie danych wyjściowych zostanie wyświetlony następujący tekst:

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

1. Otwórz okno dialogowe właściwości projektu. W sekcji **Właściwości konfiguracji** > **Ogólne** Zwróć uwagę na wartości **wersji platformy docelowej systemu Windows**. Zmiana wartości w tym miejscu ma taki sam skutek jak w przypadku tej procedury. Aby uzyskać więcej informacji, zobacz [Ogólne strony właściwości (projekt)](../build/reference/general-property-page-project.md).

   ![Wersja platformy docelowej](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Ta akcja zmienia wartości makr projektu, które zawierają ścieżki do plików nagłówkowych i plików bibliotek. Aby zobaczyć, co zostało zmienione, Otwórz sekcję **wizualizacje C++ katalogów** okna dialogowego **właściwości projektu** . Wybierz jedną z właściwości, taką jak **dołączanie katalogów**. Następnie otwórz listę rozwijaną wartość właściwości, a następnie wybierz pozycję **\<edytuj >** . Zostanie wyświetlone okno dialogowe **dołączanie katalogów** .

   ![Okno dialogowe dołączania katalogów](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Wybierz przycisk **makra > >** , a następnie przewiń w dół listę makr do Windows SDK makra, aby wyświetlić wszystkie nowe wartości.

   ![Makra Windows SDK](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

1. Powtórz procedurę przekierowania dla innych projektów rozwiązań, w razie potrzeby, a następnie Skompiluj ponownie rozwiązanie.

### <a name="to-target-the-windows-81-sdk"></a>Aby określić zestaw SDK Windows 8.1

1. Otwórz menu skrótów dla węzła projektu w Eksplorator rozwiązań i wybierz pozycję **Przekieruj projekty**. (We wcześniejszych wersjach programu Visual Studio wybierz pozycję **Przekieruj wersję zestawu SDK**).

2. Z listy rozwijanej **wersja platformy docelowej** wybierz pozycję **8,1**.

## <a name="see-also"></a>Zobacz także

[Przewodnik: Tworzenie tradycyjnej aplikacji klasycznej systemu WindowsC++()](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)
