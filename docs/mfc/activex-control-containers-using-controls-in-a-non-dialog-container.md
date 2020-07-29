---
title: 'Kontenery kontrolek ActiveX: używanie kontrolek w kontenerze innym niż okno dialogowe'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: f3f0bc7c89ff2bea1c344f2c876e1624ba82fb87
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214168"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Kontenery kontrolek ActiveX: używanie kontrolek w kontenerze innym niż okno dialogowe

W niektórych aplikacjach, takich jak aplikacja SDI lub MDI, trzeba osadzić kontrolkę w oknie aplikacji. Funkcja **Create** member klasy otoki, wstawiona przez Visual C++, może dynamicznie tworzyć wystąpienie formantu, bez potrzeby okna dialogowego.

Funkcja **Create** member ma następujące parametry:

*lpszWindowName*<br/>
Wskaźnik do tekstu, który ma być wyświetlany w właściwości tekst lub etykieta kontrolki (jeśli istnieje).

*dwStyle*<br/>
Style systemu Windows. Aby uzyskać pełną listę, zobacz [CWnd:: IsControl](reference/cwnd-class.md#createcontrol).

*cinania*<br/>
Określa rozmiar i położenie kontrolki.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki, zazwyczaj a `CDialog` . Nie może mieć **wartości null**.

*nID*<br/>
Określa identyfikator kontrolki i może być używany przez kontener w celu odwoływania się do kontrolki.

Przykładem użycia tej funkcji do dynamicznego tworzenia kontrolki ActiveX będzie w widoku formularza aplikacji SDI. Następnie można utworzyć wystąpienie kontrolki w programie `WM_CREATE` obsługi aplikacji.

W tym przykładzie `CMyView` jest klasą widoku głównego, `CCirc` jest klasą otoki i cyklem. H jest nagłówkiem (. H) plik klasy otoki.

Implementowanie tej funkcji jest procesem dwuetapowym.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Aby dynamicznie utworzyć formant ActiveX w oknie innym niż okno dialogowe

1. Wstaw cykl. H w CMYVIEW. H, tuż przed `CMyView` definicją klasy:

   [!code-cpp[NVC_MFC_AxCont#12](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Dodaj zmienną członkowską (typu `CCirc` ) do chronionej sekcji `CMyView` definicji klasy znajdującej się w CMYVIEW. C

   [!code-cpp[NVC_MFC_AxCont#13](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Dodaj `WM_CREATE` procedurę obsługi komunikatów do klasy `CMyView` .

1. W funkcji obsługi, należy `CMyView::OnCreate` wywołać funkcję kontrolki `Create` przy użyciu **`this`** wskaźnika jako okna nadrzędnego:

   [!code-cpp[NVC_MFC_AxCont#15](codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Ponownie skompiluj projekt. Kontrolka cykl zostanie utworzona dynamicznie za każdym razem, gdy zostanie utworzony widok aplikacji.

## <a name="see-also"></a>Zobacz także

[Kontenery kontrolek ActiveX](activex-control-containers.md)
