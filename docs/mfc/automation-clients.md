---
title: Klienci automatyzacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4a4327e1c3e4d65c5bdc3b822cf2cdfc1ec0353
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820597"
---
# <a name="automation-clients"></a>Klienci automatyzacji

Automatyzacja sprawiają, że aplikacja do manipulowania obiektami implementowane w innej aplikacji lub do udostępnienia obiektów, dzięki czemu można manipulować. Klienta automatyzacji to aplikacja, który będzie obsługiwał widocznych obiektów należących do innej aplikacji. Aplikacja, która udostępnia obiekty nosi nazwę serwera automatyzacji. Klient obsługuje obiekty aplikacji serwera, uzyskując dostęp do właściwości te obiekty i funkcje.

### <a name="types-of-automation-clients"></a>Typy klientów automatyzacji

Istnieją dwa typy klientów automatyzacji:

- Klienci, którzy dynamicznie (w czasie wykonywania) uzyskiwanie informacji na temat właściwości i operacji serwera.

- Klienci, którzy posiadają dostarczonymi informacjami statycznymi (w czasie kompilacji) określający, właściwości i operacji serwera.

Klienci pierwszy rodzaj uzyskania informacji na temat metod i właściwości serwera, badając OLE system `IDispatch` mechanizm. Mimo że jest odpowiedni do użycia dla klientów dynamicznych `IDispatch` jest trudny do użycia na potrzeby klientów statycznych, których obiekty są oparte na musi być znane, na czas kompilacji. Statyczna powiązana klientów, Microsoft Foundation classes zapewnianych [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) klasy.

Statyczne powiązanej klienci używają klasy serwera proxy, statycznie połączoną z aplikacją klienta. Ta klasa udostępnia bezpieczny hermetyzacji C++, właściwości i operacji aplikacji serwera.

Klasa `COleDispatchDriver` zapewnia obsługę jednostki po stronie klienta automatyzacji. Za pomocą **Dodaj nowy element** okno dialogowe, należy utworzyć klasę pochodną `COleDispatchDriver`.

Następnie możesz określić plik biblioteki typów, opisujący właściwości i funkcje obiektu aplikacji serwera. Okno dialogowe Dodaj element odczytuje ten plik i tworzy `COleDispatchDriver`-klasy za pomocą funkcji Członkowskich, które aplikacja może wywołać dostępu do aplikacji serwera obiektów w języku C++ w sposób bezpieczny. Dodatkowe funkcje odziedziczone `COleDispatchDriver` upraszcza proces wywoływania właściwego serwera automatyzacji.

### <a name="handling-events-in-automation-clients"></a>Obsługa zdarzeń w klientach automatyzacji

Do obsługi zdarzeń w kliencie usługi automation, musisz dodać interfejs ujścia. MFC obsługuje kreatora Dodaj interfejsy ujścia dla kontrolek ActiveX, ale nie dla innych serwerów COM. Instrukcje dotyczące sposobu dodawania interfejs obiektu sink w kliencie interfejsy źródła opisanego przez serwery COM MFC, zobacz porady: Utworzenie interfejsu ujścia w kliencie COM MFC-Based (KB 181845) na [ http://support.microsoft.com/default.aspxscid=kb; 181845](http://support.microsoft.com/default.aspxscid=kb;181845).

## <a name="see-also"></a>Zobacz też

[Klienci automatyzacji: korzystanie z bibliotek typów](../mfc/automation-clients-using-type-libraries.md)<br/>
[Automatyzacja](../mfc/automation.md)<br/>
[Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md)

