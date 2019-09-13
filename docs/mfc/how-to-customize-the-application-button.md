---
title: 'Instrukcje: Dostosuj przycisk aplikacji'
ms.date: 09/07/2019
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: 3a1d1625e80e6c6f4440864629a5123bed5744c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907787"
---
# <a name="how-to-customize-the-application-button"></a>Instrukcje: Dostosuj przycisk aplikacji

Po kliknięciu przycisku aplikacji wyświetlane jest menu poleceń. Zwykle menu zawiera polecenia związane z plikiem, takie jak **Otwórz**, **Zapisz**, **Drukuj**i **Wyjdź**.

![Przycisk aplikacji wstążki MFC](../mfc/media/application_button.png "Przycisk aplikacji wstążki MFC")

Aby dostosować przycisk aplikacji, otwórz go w oknie **Właściwości** (w **Widok zasobów**), zmodyfikuj jego właściwości, a następnie Wyświetl podgląd kontrolki wstążki.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Aby otworzyć przycisk aplikacji w okno Właściwości

1. W programie Visual Studio, w menu **Widok** kliknij **Widok zasobów**.

1. W **Widok zasobów**kliknij dwukrotnie zasób wstążki, aby wyświetlić go na powierzchni projektowej.

1. Na powierzchni projektowej kliknij prawym przyciskiem myszy przycisk aplikacji menu, a następnie kliknij polecenie **Właściwości**.

## <a name="application-button-properties"></a>Właściwości przycisku aplikacji

W poniższej tabeli zdefiniowano właściwości przycisku aplikacji.

|Właściwość|Definicja|
|--------------|----------------|
|**Przyciski**|Zawiera kolekcję maksymalnie trzech przycisków, które są wyświetlane w prawym dolnym rogu menu aplikacji.|
|**Caption**|Określa tekst kontrolki. W przeciwieństwie do innych elementów wstążki przycisk aplikacji nie wyświetla tekstu napisów. Zamiast tego tekst jest używany na potrzeby ułatwień dostępu.|
|**Obraz HDPI**|Określa identyfikator ikony przycisku aplikacji o dużej liczbie kropek na cal (HDPI). Gdy aplikacja jest uruchamiana na monitorze o wysokiej rozdzielczości DPI, zamiast **obrazu**jest używany **obraz HDPI** .|
|**HDPI duże obrazy**|Określa identyfikator dużych obrazów o dużej rozdzielczości DPI. Gdy aplikacja jest uruchamiana na monitorze o wysokiej rozdzielczości DPI, zamiast **dużych obrazów**jest używana **HDPI duże obrazy** .|
|**HDPI małe obrazy**|Określa identyfikator małych obrazów o wysokiej rozdzielczości DPI. Gdy aplikacja działa w monitorze o wysokiej rozdzielczości DPI, zamiast **małych obrazów**jest używane **HDPI małe obrazy** .|
|**Identyfikator**|Określa identyfikator kontrolki.|
|**Obraz**|Określa identyfikator ikony przycisku aplikacji. Ikona to 32-bitowa Mapa bitowa 26x26 o przezroczystości alfa. Przezroczyste fragmenty ikony są wyróżniane po kliknięciu przycisku aplikacji lub umieszczeniu na nim wskaźnika myszy.|
|**Ponownie**|Określa ciąg, który jest wyświetlany, gdy jest włączona Nawigacja przy użyciu etykietek. Nawigacja po kluczu jest włączona po naciśnięciu klawisza ALT.|
|**Duże obrazy**|Określa identyfikator obrazu, który zawiera serię ikon 32x32. Ikony są używane przez przyciski w kolekcji Main Items.|
|**Elementy główne**|Zawiera kolekcję elementów menu, które są wyświetlane w menu aplikacji.|
|**Podpis MRU**|Określa tekst wyświetlany w panelu listy ostatnio używanych.|
|**Małe obrazy**|Określa identyfikator obrazu, który zawiera serię 16x16 ikon. Ikony są używane przez przyciski w kolekcji przyciski.|
|**Korzystanie**|Włącza lub wyłącza panel listy ostatnio używanych. Panel Lista ostatnio pojawia się w menu aplikacji.|
|**Szerokość**|Określa szerokość (w pikselach) ostatniego panelu listy.|

Menu aplikacji nie jest wyświetlane na powierzchni projektowej. Aby je wyświetlić, należy wyświetlić podgląd wstążki lub uruchomić aplikację.

#### <a name="to-preview-the-ribbon-control"></a>Aby wyświetlić podgląd kontrolki wstążki

- Na **pasku narzędzi edytora wstążki**kliknij pozycję **Testuj wstążka**.

## <a name="see-also"></a>Zobacz także

[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)
