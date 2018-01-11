---
title: "Wywoływanie kodu C++ z DHTML | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e2d0da431249ef886ceca1e2b7f6cbfc99418dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="calling-c-code-from-dhtml"></a>Wywoływanie kodu w języku C++ z DHTML
Formant DHTML może być hostowana w kontenerze, takich jak kontener testu lub program Internet Explorer. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat sposobu dostępu kontener testu.  
  
 Hosting formantu kontenera komunikuje się za pomocą formantu przy użyciu interfejsów normalnej kontroli. DHTML używa interfejsu wysyłania, która kończy się wyrazem "UI" do komunikowania się z kodu C++ i zasobu HTML. W [modyfikacji formantu ATL DHTML](../atl/modifying-the-atl-dhtml-control.md), ćwiczenie Dodawanie metody do wywołania przez te interfejsy.  
  
 Aby wyświetlić przykład wywoływanie kodu w języku C++ z DHTML, [Tworzenie formantu DHTML](../atl/creating-an-atl-dhtml-control.md) służy Kreator formantu ATL i sprawdź, czy kod w pliku nagłówka i w pliku w formacie HTML.  
  
## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Deklarowanie WebBrowser metody w pliku nagłówka  
 Do wywołania metody C++ z DHTML interfejsu użytkownika, należy dodać metod formantu interfejsu użytkownika interfejsu. Na przykład plik nagłówka utworzone przez Kreator formantu ATL zawiera metodę C++ `OnClick`, który jest elementem członkowskim interfejsu interfejsu użytkownika formantu generowane przez kreatora.  
  
 Sprawdź `OnClick` w pliku .h formantu:  
  
 [!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]  
  
 Pierwszy parametr `pdispBody`, jest wskaźnik do obiektu treści interfejs wysyłania. Drugi parametr `varColor`, określa kolor do formantu.  
  
## <a name="calling-c-code-in-the-html-file"></a>Wywoływanie kodu C++ w pliku HTML  
 Po zadeklarowaniu metody WebBrowser w pliku nagłówka, można wywoływać metod z pliku HTML. W pliku HTML powiadomienie, że Kreator formantu ATL wstawia trzy Windows metody wysyłania: trzy `OnClick` metod, które wysyłają komunikaty, aby zmienić kolor tła formantu.  
  
 Sprawdź jednej z metod w pliku w formacie HTML:  
  
 `<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`  
  
 W kodzie HTML powyżej okna zewnętrzną metodę `OnClick`, jest wywoływana w ramach tagu przycisku. Metoda ma dwa parametry: `theBody`, który odwołuje się do dokumentu HTML i `"red"`, co oznacza, że kolor tła formantu zostanie zmieniony na czerwony po kliknięciu przycisku. `Red` Po tagu jest etykieta przycisku.  
  
 Zobacz [modyfikacji formantu ATL DHTML](../atl/modifying-the-atl-dhtml-control.md) Aby uzyskać więcej informacji na temat podawania własne metody. Zobacz [określający elementy projektu kontroli DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) uzyskać więcej informacji o pliku w formacie HTML.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa dla DHTML](../atl/atl-support-for-dhtml-controls.md)

