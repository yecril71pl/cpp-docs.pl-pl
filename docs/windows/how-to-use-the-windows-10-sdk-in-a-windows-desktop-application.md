---
title: 'Instrukcje: Użyj systemu Windows 10 SDK w aplikacji pulpitu Windows'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: f3f6897dfa0f180f629a2ca169ff74c5e5588365
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351013"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Instrukcje: Użyj systemu Windows 10 SDK w aplikacji pulpitu Windows

Po utworzeniu klasycznego projektu pulpitu Windows w programie Visual Studio 2017 on skonfigurowano domyślnie do tworzenia z wersją systemu Windows 10 SDK został zainstalowany, gdy obciążenie C++ na komputerach został zainstalowany lub jego ostatniej aktualizacji. Ta wersja zestawu Windows SDK jest zgodny, system Windows 7 lub nowszy. Zobacz [przy użyciu nagłówków Windows](/windows/desktop/WinProg/using-the-windows-headers) Aby uzyskać więcej informacji na temat przeznaczony dla określonej wersji systemu Windows.

Jeśli chcesz przeanalizować wcześniejszej wersji zestawu SDK, możesz otworzyć **projektu | Właściwości** i wybierz jedną z dostępnych w menu rozwijanym wersja zestawu SDK Windows wersji zestawu SDK.

Począwszy od programu Visual Studio 2015 i zestawu Windows 10 SDK, biblioteki CRT zostało podzielone na dwie części: outside (ucrtbase) zawiera funkcje, które są akceptowane można używać w Universal Windows Apps i która zawiera wszystkie inne elementy (vcruntime140). Ponieważ zestawu Windows 10 SDK zawiera nowe funkcje, takie jak wiele funkcji C99, musisz wykonaj następujące kroki, aby można było używać tych funkcji. Zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

### <a name="to-target-the-windows-10-sdk"></a>Do obiektu docelowego zestawu Windows 10 SDK

1. Upewnij się, że zainstalowano zestaw SDK systemu Windows 10. Windows 10 SDK jest zainstalowany jako część **programowanie aplikacji klasycznych w języku C++** obciążenia. Wersja autonomiczna jest dostępna w [pliki do pobrania i narzędzia dla systemu Windows 10](https://developer.microsoft.com/windows/downloads).

2. Otwórz menu skrótów dla węzła projektu, a następnie wybierz **przekierowanie wersji zestawu SDK**.

   ![Przekierowanie wersji zestawu SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   **Przegląd akcji rozwiązania** zostanie wyświetlone okno dialogowe.

   ![Przegląd akcji rozwiązania](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. W **wersji platformy docelowej** listy rozwijanej wybierz wersję docelową zestawu Windows 10 SDK. Wybierz przycisk OK, aby zastosować zmiany.

   Należy pamiętać, że 8.1, w tym kontekście odwołuje się do wersji zestawu Windows SDK, który również jest wstecznie zgodne z systemem Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 i Windows Vista.

   Jeśli ten krok zakończy się pomyślnie, w oknie danych wyjściowych zostanie wyświetlony następujący tekst:

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. Otwórz właściwości projektu, a następnie w **właściwości konfiguracji, ogólne** sekcji, zwróć uwagę na wartości z **wersji platformy docelowej Windows**. Zmiana wartości w tym miejscu ma taki sam skutek jak następującej procedury. Zobacz [strona właściwości ogólnych (projekt)](../build/reference/general-property-page-project.md).

   ![Wersja platformy docelowej](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Ta akcja powoduje zmianę wartości makra projektu, które zawierają ścieżki do plików biblioteki i pliki nagłówkowe. Aby zobaczyć, co zmieniło w **katalogi Visual C++** części **właściwości projektu** okno dialogowe, wybierz jedną z właściwości, takie jak **Dołącz katalogi**, wybrać opcję Otwórz listę rozwijaną i wybierz polecenie \<Edytuj >. **Dołącz katalogi** zostanie wyświetlone okno dialogowe.

   ![Obejmują katalogi, okno dialogowe](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Wybierz **makra >>** przycisk, a następnie przewiń w dół listę makra do makr zestawu Windows SDK, aby zobaczyć nowe wartości.

   ![Windows SDK makra](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. Powtarzaj tę procedurę dla innych projektów i ponownie skompiluj rozwiązanie.

### <a name="to-target-the-windows-81-sdk"></a>Docelowy zestaw SDK Windows 8.1

1. Otwórz menu skrótów dla węzła projektu, a następnie wybierz **przekierowanie wersji zestawu SDK**.

2. W **wersji platformy docelowej** listy rozwijanej wybierz **8.1**.

## <a name="see-also"></a>Zobacz także

[Windows aplikacji komputerowych (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)