---
title: 'Kontrolki ActiveX MFC: tworzenie serwera automatyzacji'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: 6861d8b0798ece957c84f52a15032052aa83b9c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448129"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Kontrolki ActiveX MFC: tworzenie serwera automatyzacji

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

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

