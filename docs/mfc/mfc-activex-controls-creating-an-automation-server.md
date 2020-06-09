---
title: 'Formanty MFC ActiveX: tworzenie serwera automatyzacji'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: f2c941e43e810845560b4c35c558ec70248c21ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622380"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Formanty MFC ActiveX: tworzenie serwera automatyzacji

Formant ActiveX MFC można opracowywać jako serwer automatyzacji na potrzeby programistycznego osadzania tej kontrolki w innej aplikacji i wywoływania metod w formancie z aplikacji. Taki formant nadal będzie dostępny do hostowania w kontenerze kontrolek ActiveX.

### <a name="to-create-a-control-as-an-automation-server"></a>Aby utworzyć kontrolkę jako serwer automatyzacji

1. [Utwórz](reference/mfc-activex-control-wizard.md) formant.

1. [Dodawanie metod](mfc-activex-controls-methods.md).

1. Zastąp [IsInvokeAllowed](reference/colecontrol-class.md#isinvokeallowed).

1. Kompiluj formant.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Aby programowo uzyskać dostęp do metod na serwerze automatyzacji

1. Utwórz aplikację, na przykład plik [exe MFC](reference/mfc-application-wizard.md).

1. Na początku `InitInstance` funkcji Dodaj następujący wiersz:

   [!code-cpp[NVC_MFC_AxCont#17](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. W Widok klasy kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj klasę z biblioteki typów** , aby zaimportować bibliotekę typów.

   Spowoduje to dodanie plików z rozszerzeniami nazw plików. h i. cpp do projektu.

1. W pliku nagłówkowym klasy, w której będzie wywoływana jedna lub więcej metod w kontrolce ActiveX, Dodaj następujący wiersz: `#include filename.h` , gdzie nazwa pliku jest nazwą pliku nagłówkowego, który został utworzony podczas importowania biblioteki typów.

1. W funkcji, w której zostanie wykonane wywołanie metody w kontrolce ActiveX, Dodaj kod, który tworzy obiekt klasy otoki kontrolki i Utwórz obiekt ActiveX. Na przykład poniższy kod MFC tworzy wystąpienie `CCirc` kontrolki, pobiera właściwość Caption i wyświetla wynik po kliknięciu przycisku OK w oknie dialogowym:

   [!code-cpp[NVC_MFC_AxCont#18](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Jeśli dodasz metody do kontrolki ActiveX po użyciu jej w aplikacji, możesz zacząć korzystać z najnowszej wersji kontrolki w aplikacji, usuwając pliki, które zostały utworzone podczas importowania biblioteki typów. Następnie ponownie zaimportuj bibliotekę typów.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
