---
title: 'Kontenery kontrolek ActiveX: Używanie kontrolek w kontenerze innym niż okno dialogowe'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: 70a67a6952d5361177b89e3ba514d7036b5799b6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284245"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Kontenery kontrolek ActiveX: Używanie kontrolek w kontenerze innym niż okno dialogowe

W niektórych aplikacji, takich jak SDI lub MDI aplikacji należy osadzić formantu w oknie aplikacji. **Utwórz** funkcji składowej klasy otoki wstawione przez Visual C++, można utworzyć wystąpienie kontrolki dynamicznie, bez konieczności dla okna dialogowego.

**Utwórz** funkcja elementu członkowskiego ma następujące parametry:

*lpszWindowName*<br/>
Wskaźnik na tekst do wyświetlenia we właściwości Text lub Caption kontrolki (jeśli istnieje).

*dwStyle*<br/>
Style Windows. Aby uzyskać pełną listę, zobacz [CWnd::CreateControl](../mfc/reference/cwnd-class.md#createcontrol).

*Rect*<br/>
Określa rozmiar i położenie formantu.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki, zwykle `CDialog`. Nie może być **NULL**.

*nID*<br/>
Określa identyfikator kontrolki i może służyć przez kontener do odwoływania się do kontrolki.

Przykładem korzystania z tej funkcji umożliwia dynamiczne tworzenie formantu ActiveX byłoby w widoku formularza aplikacji interfejsu SDI. Następnie można utworzyć wystąpienia kontrolki `WM_CREATE` obsługi aplikacji.

W tym przykładzie `CMyView` jest klasą Widok główny `CCirc` to klasa otoki i okólnik H jest nagłówkiem, którego (. H) plik klasy otoki.

Implementacja tej funkcji jest procesem, krok 4.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Umożliwia dynamiczne tworzenie kontrolki ActiveX w oknie innym niż okno dialogowe

1. Wstaw okólnik H w CMYVIEW. Godz., tuż przed `CMyView` definicję klasy:

   [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Dodawanie zmiennej członkowskiej (typu `CCirc`) do sekcji chronionych `CMyView` na terenie CMYVIEW definicji klasy. GODZ.:

   [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Dodaj `WM_CREATE` obsługi wiadomości do klasy `CMyView`.

1. W funkcji obsługi `CMyView::OnCreate`, wywołanie formantu `Create` funkcję za pomocą **to** wskaźnik jako okno nadrzędne:

   [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Skompiluj ponownie projekt. Kontrolka OK zostanie utworzony dynamicznie po każdym utworzeniu widoku aplikacji.

## <a name="see-also"></a>Zobacz także

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
