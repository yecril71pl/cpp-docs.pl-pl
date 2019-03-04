---
title: 'Instrukcje: Dostosowywanie przycisku aplikacja'
ms.date: 11/19/2018
helpviewer_keywords:
- application button [MFC], customizing
ms.assetid: ebb11180-ab20-43df-a234-801feca9eb38
ms.openlocfilehash: d45ceaf1cce21f77871e966e0e8f525f95cb4c37
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269542"
---
# <a name="how-to-customize-the-application-button"></a>Instrukcje: Dostosowywanie przycisku aplikacja

Po kliknięciu przycisku aplikacja, jest wyświetlany menu poleceń. Zazwyczaj menu zawiera polecenia związane z plików takich jak **Otwórz**, **Zapisz**, **drukowania**, i **zakończenia**.

![Przycisk aplikacji wstążki MFC](../mfc/media/application_button.png "przycisku aplikacja wstążki MFC")

Dostosowywanie przycisku aplikacja, otwórz go w **właściwości** , zmodyfikuj jego właściwości, a następnie Wyświetl podgląd formantu wstążki.

### <a name="to-open-the-application-button-in-the-properties-window"></a>Aby otworzyć przycisku aplikacji w oknie dialogowym właściwości

1. W programie Visual Studio na **widoku** menu, kliknij przycisk **widok zasobów**.

1. W **widok zasobów**, kliknij dwukrotnie zasób wstążki, aby wyświetlić je na powierzchni projektowej.

1. Na powierzchni projektowej kliknij prawym przyciskiem myszy menu przycisku aplikacji, a następnie kliknij przycisk **właściwości**.

## <a name="application-button-properties"></a>Właściwości przycisku w aplikacji

W poniższej tabeli opisano właściwości przycisku aplikacji.

|Właściwość|Definicja|
|--------------|----------------|
|**Przyciski**|Zawiera kolekcję maksymalnie trzy przyciski, które pojawiają się w prawym dolnym rogu menu aplikacji.|
|**Podpis**|Określa tekst kontrolki. W przeciwieństwie do innych elementów wstążki przycisku aplikacji nie jest wyświetlany tekst podpisu. Zamiast tego tekst jest używany w ułatwienia dostępu.|
|**Obraz HDPI**|Określa identyfikator wysokie dpi ikona przycisku (HDPI) aplikacji. Gdy aplikacja zostanie uruchomiona na monitorze wysokiej rozdzielczości DPI **obraz HDPI** jest używana zamiast **obraz**.|
|**Duże obrazy HDPI**|Określa identyfikator o wysokiej rozdzielczości DPI dużych obrazów. Gdy aplikacja zostanie uruchomiona na monitorze wysokiej rozdzielczości DPI **duże obrazy HDPI** jest używana zamiast **duże obrazy**.|
|**Małe obrazy HDPI**|Określa identyfikator o wysokiej rozdzielczości DPI małe obrazy. Gdy aplikacja zostanie uruchomiona na monitorze wysokiej rozdzielczości DPI **małe obrazy HDPI** jest używana zamiast **małe obrazy**.|
|**Identyfikator**|Określa identyfikator kontrolki.|
|**Obraz**|Określa identyfikator ikony przycisku aplikacji. Ikona jest mapą bitową 26 x 26 32-bitowych, zawierającej alfa przezroczystości. Po kliknięciu przycisku aplikacji lub najechania kursorem, zostały wyróżnione przezroczyste obiekty ikony.|
|**klucze**|Określa ciąg, który jest wyświetlany, gdy porada klucz Nawigacja jest włączona. Porada klucz nawigacji jest włączona po naciśnięciu klawisza ALT.|
|**Duże obrazy**|Określa identyfikator obrazu, który zawiera szereg ikony 32 x 32. Ikony są używane przez przycisków w kolekcji elementów Main.|
|**Elementy główne**|Zawiera kolekcję elementów menu, które są wyświetlane w menu aplikacji.|
|**Podpis MRU**|Określa tekst wyświetlany na panelu listy ostatnio używanych.|
|**Małe obrazy**|Określa identyfikator obrazu, który zawiera szereg ikony 16 x 16. Ikony są używane przez przycisków w kolekcji przycisków.|
|**Korzystanie**|Włącza lub wyłącza panel listy ostatnio używanych. W menu aplikacji zostanie wyświetlony panel listy ostatnio używanych.|
|**Szerokość**|Określa szerokość w pikselach na panelu listy ostatnio używanych.|

W menu aplikacji nie jest wyświetlana na powierzchni projektowej. Aby ją wyświetlić, możesz przeglądanie Wstążki lub uruchomić aplikację.

#### <a name="to-preview-the-ribbon-control"></a>Aby wyświetlić podgląd formantu wstążki

- Na **pasek narzędzi edytora wstążki**, kliknij przycisk **Testuj Wstążkę**.

## <a name="see-also"></a>Zobacz także

[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)
