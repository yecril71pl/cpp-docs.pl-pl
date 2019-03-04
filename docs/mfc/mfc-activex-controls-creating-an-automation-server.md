---
title: 'Kontrolki ActiveX MFC: Tworzenie serwera automatyzacji'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: 01f0162e124c5c49d45ce4a90f5243c88b09b5a0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303732"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Kontrolki ActiveX MFC: Tworzenie serwera automatyzacji

Kontrolki MFC ActiveX można tworzyć jako serwer automatyzacji na potrzeby programowo osadzania tę kontrolkę w innej aplikacji, a w przypadku wywoływania metod kontroli aplikacji. Kontrolka nadal będą dostępne hostowane w kontenerze kontrolek ActiveX.

### <a name="to-create-a-control-as-an-automation-server"></a>Aby utworzyć kontrolkę jako serwer automatyzacji

1. [Utwórz](../mfc/reference/mfc-activex-control-wizard.md) formantu.

1. [Dodaj metody](../mfc/mfc-activex-controls-methods.md).

1. Zastąp [IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed).

1. Kompiluj wersję.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Aby uzyskać programowy dostęp do metod w serwera automatyzacji

1. Utwórz aplikację, na przykład, [MFC exe](../mfc/reference/mfc-application-wizard.md).

1. Na początku `InitInstance` funkcji, Dodaj następujący wiersz:

   [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. W widoku klas kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **dodawania klasy z typelib** do importowania biblioteki typów.

   Spowoduje to dodanie plików .cpp i .h rozszerzenia nazwy pliku do projektu.

1. W pliku nagłówkowym klasy, gdzie będzie wywoływać co najmniej jednej metody w formancie ActiveX, Dodaj następujący wiersz: `#include filename.h`, gdzie nazwa pliku to nazwa pliku nagłówkowego, który został utworzony podczas importowania biblioteki typów.

1. W funkcji, w którym nastąpi wywołanie do metody w formancie ActiveX Dodaj kod, który tworzy obiekt klasy otoki kontrolki i Utwórz obiekt ActiveX. Na przykład, poniższy kod MFC tworzy `CCirc` formant, który pobiera właściwości podpisu i wyświetla wynik, po kliknięciu przycisku OK w oknie dialogowym:

   [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Jeśli dodasz metody do formantu ActiveX, zostanie użyta w aplikacji, możesz rozpocząć korzystanie z najnowszej wersji kontroli w aplikacji, usuwając pliki, które zostały utworzone podczas importowania biblioteki typów. Następnie ponownie zaimportuj bibliotekę typów.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
