---
title: 'Porady: konwertowanie istniejącej wstążki MFC na zasób wstążki'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 56f36c977453d338b9e9bbd2462c1a8830ffe258
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620050"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Porady: konwertowanie istniejącej wstążki MFC na zasób wstążki

Zasoby wstążki są łatwiejsze do wizualizacji, modyfikowania i konserwowania niż ręcznie zakodowane wstążki. W tym temacie opisano sposób konwertowania ręcznie zakodowanej wstążki w projekcie MFC do zasobu wstążki.

Musisz mieć istniejący projekt MFC, który ma kod korzystający z klas wstążki MFC, na przykład [Klasa CMFCRibbonBar](reference/cmfcribbonbar-class.md).

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Aby skonwertować Wstążkę MFC na zasób wstążki

1. W programie Visual Studio, w istniejącym projekcie MFC, Otwórz plik źródłowy, w którym `CMFCRibbonBar` obiekt jest zainicjowany. Zwykle plik to MainFrm. cpp. Dodaj następujący kod po kodzie inicjalizacji wstążki.

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");
```

   Zapisz i zamknij plik.

1. Skompiluj i uruchom aplikację MFC, a następnie w Notatniku otwórz RibbonOutput. txt i skopiuj jej zawartość.

1. W programie Visual Studio w menu **projekt** kliknij polecenie **Dodaj zasób**. W oknie dialogowym **Dodawanie zasobu** wybierz **Wstążkę** , a następnie kliknij przycisk **Nowy**.

   Program Visual Studio tworzy zasób wstążki i otwiera go w widoku projektu. Identyfikator zasobu wstążki to IDR_RIBBON1, który jest wyświetlany w **Widok zasobów**. Wstążka jest zdefiniowana w pliku XML Ribbon1. mfcribbon-ms.

1. W programie Visual Studio Otwórz Ribbon1. mfcribbon-ms, usuń jego zawartość, a następnie wklej zawartość RibbonOutput. txt, która została wcześniej skopiowana. Zapisz i Zamknij Ribbon1. mfcribbon-ms.

1. Ponownie otwórz plik źródłowy, w którym zainicjowano obiekt CMFCRibbonBar (zazwyczaj MainFrm. cpp) i Dodaj komentarz do istniejącego kodu wstążki. Dodaj następujący kod po komentarzu do kodu.

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
```

1. Skompiluj projekt i uruchom program.

## <a name="see-also"></a>Zobacz też

[Projektant wstążki (MFC)](ribbon-designer-mfc.md)
