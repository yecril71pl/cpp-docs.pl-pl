---
title: "Używanie pól wywołania zwrotnego w selektora dat i godzin kontrolki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
dev_langs: C++
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e5526b0f8826a91eb0b1c5a6eae250abbb02fcf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Używanie pól wywołania zwrotnego w formancie selektora dat i godzin
Oprócz standardowych format znaków, które definiują pola selektora daty i godziny dane wyjściowe można dostosować, określając niektórych części ciągu formatu niestandardowego pola wywołania zwrotnego. Aby zadeklarować pole wywołania zwrotnego, zawierają co najmniej jeden znak "X" (88 kodu ASCII) dowolne miejsce w treści ciąg formatu. Na przykład, następujący ciąg "" obecnie jest: "yy" / "MM" / "dd" (dzień "X") ""powoduje, że formant wyboru daty i godziny wyświetlić bieżącą wartość jako rok, miesiąc, datę oraz finally dzień roku.  
  
> [!NOTE]
>  Liczba znakiem x w wywołaniu zwrotnym pola nie odpowiada liczbie znaków, które będą wyświetlane.  
  
 Można rozróżnić wiele pól wywołania zwrotnego w ciągu niestandardowego przez powtarzanie znak "X". W związku z tym ciągu formatu "XXddddMMMdd", "yyyXXX" zawiera dwa pola Unikatowy wywołania zwrotnego "XX" i "XXX".  
  
> [!NOTE]
>  Pola wywołania zwrotnego są traktowane jako prawidłowe pola, więc aplikacji muszą być przygotowane do obsługi **DTN_WMKEYDOWN** komunikaty powiadomień.  
  
 Implementowanie pola wywołania zwrotnego w formant wyboru daty i godziny składa się z trzech części:  
  
-   Inicjowanie niestandardowy ciąg formatu  
  
-   Obsługa **dtn_formatquery —** powiadomień  
  
-   Obsługa **dtn_format —** powiadomień  
  
## <a name="initializing-the-custom-format-string"></a>Inicjowanie niestandardowy ciąg formatu  
 Inicjuje ciąg niestandardowy z wywołaniem do `CDateTimeCtrl::SetFormat`. Aby uzyskać więcej informacji, zobacz [przy użyciu niestandardowe ciągi formatów daty i czasu formant wyboru](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Spójne ustawiony niestandardowy ciąg formatu jest `OnInitDialog` funkcja zawierające klasy okien dialogowych lub `OnInitialUpdate` funkcja zawierające klasy widoku.  
  
## <a name="handling-the-dtnformatquery-notification"></a>Obsługa dtn_formatquery — powiadomienie  
 Gdy formant analizuje ciąg formatu i napotka pola wywołania zwrotnego, wysyła aplikacji **dtn_format —** i **dtn_formatquery —** komunikaty powiadomień. Ciąg pola wywołania zwrotnego jest dołączana do powiadomień, dzięki czemu można określić pole wywołania zwrotnego, które dotyczy zapytanie.  
  
 **Dtn_formatquery —** powiadomienie jest wysyłane do pobrania maksymalny dozwolony rozmiar w pikselach ciąg, który będzie wyświetlany w polu bieżącego wywołania zwrotnego.  
  
 Aby poprawnie obliczyć tej wartości, musisz obliczyć wysokość i szerokość ciągu znaków do zastąpienia dla pola przy użyciu czcionki wyświetlania formantu. Rzeczywiste obliczenia ciągu jest łatwo uzyskać przy użyciu wywołania [GetTextExtentPoint32](http://msdn.microsoft.com/library/windows/desktop/dd144938) funkcji Win32. Po określeniu rozmiar wartość należy przekazać do aplikacji i zakończyć działanie funkcji obsługi.  
  
 Poniższy przykład jest jedna z metod rozmiar ciągu wywołania zwrotnego podawania:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]  
  
 Po obliczeniu rozmiar bieżącego pola wywołania zwrotnego należy podać wartość dla pola. Odbywa się w obsłudze dla **dtn_format —** powiadomień.  
  
## <a name="handling-the-dtnformat-notification"></a>Obsługa dtn_format — powiadomienie  
 **Dtn_format —** powiadomień jest używany przez aplikację na żądanie do ciągu znaków, która zostanie zastąpiona. W poniższym przykładzie pokazano jedną metodę możliwe:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]  
  
> [!NOTE]
>  Wskaźnik do **NMDATETIMEFORMAT** struktury są wyszukiwane przy rzutowanie pierwszy parametr funkcji obsługi powiadomień do odpowiedniego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

