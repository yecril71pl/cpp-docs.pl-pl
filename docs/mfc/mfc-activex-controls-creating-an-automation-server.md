---
title: 'Formanty MFC ActiveX: Tworzenie serwera automatyzacji | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56b05c85212630b8e368817006098aeff2ceb832
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>Kontrolki ActiveX MFC: tworzenie serwera automatyzacji
Kontrolki MFC ActiveX można tworzyć jako serwer automatyzacji na potrzeby programowo osadzanie tego formantu w innej aplikacji i z aplikacji podczas wywoływania metody w formancie. Takie formantu pozostaje dostępny ma być obsługiwana w kontenerze formantów ActiveX.  
  
### <a name="to-create-a-control-as-an-automation-server"></a>Aby utworzyć formant jako serwer automatyzacji  
  
1.  [Utwórz](../mfc/reference/mfc-activex-control-wizard.md) formantu.  
  
2.  [Dodaj metody](../mfc/mfc-activex-controls-methods.md).  
  
3.  Zastąpienie [IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed). Aby uzyskać więcej informacji zobacz artykuł bazy wiedzy Knowledge Base Q146120.  
  
4.  Tworzenie formantu.  
  
### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Do uzyskania programowego dostępu do metody w serwera automatyzacji  
  
1.  Tworzenie aplikacji, na przykład, [MFC exe](../mfc/reference/mfc-application-wizard.md).  
  
2.  Na początku `InitInstance` działać, Dodaj następujący wiersz:  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  W widoku klas, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **dodawania klasy z typelib** do zaimportowania do biblioteki typów.  
  
     Spowoduje to dodanie pliki .h rozszerzenia nazwy pliku i .cpp do projektu.  
  
4.  W pliku nagłówka klasy, których wywoła co najmniej jednej metody w formancie ActiveX, Dodaj następujący wiersz: `#include filename.h`, gdzie nazwa pliku jest nazwą pliku nagłówka, który został utworzony podczas importowania biblioteki typów.  
  
5.  W funkcji, których nastąpi wywołanie do metody w formancie ActiveX Dodaj kod, który tworzy obiekt klasy otoki formantu i Utwórz obiekt ActiveX. Na przykład następujący kod MFC tworzy `CCirc` formant, który pobiera właściwości podpisu i wyświetla wynik po kliknięciu przycisku OK w oknie dialogowym:  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 Jeśli dodasz metod do formantu ActiveX, po użyciu w aplikacji, możesz rozpocząć przy użyciu najnowszej wersji formantu w aplikacji, usuwając pliki, które zostały utworzone podczas importowania biblioteki typów. Następnie zaimportuj ponownie biblioteki typów.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

