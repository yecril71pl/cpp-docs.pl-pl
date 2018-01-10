---
title: Automatyzacja | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce34abd10b4681ba378cf4fbd777c96277f4db4e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="automation"></a>Automatyzacja
Automatyzacja (wcześniej znane jako automatyzacji OLE) umożliwia jednej aplikacji do modyfikowania obiektów w innej aplikacji lub na uwidocznienie obiektów, więc można manipulować.  
  
 [Serwer automatyzacji](../mfc/automation-servers.md) jest aplikacja (typ serwera COM), która udostępnia jego funkcje za pośrednictwem interfejsów COM do innych aplikacji o nazwie [klientów automatyzacji](../mfc/automation-clients.md). Narażenia umożliwia zautomatyzować niektóre funkcje przez bezpośrednie uzyskiwanie dostępu do obiektów i korzystania z usług, które zapewniają klientom automatyzacji.  
  
 Serwery automatyzacji i klienci korzystają z interfejsów modelu COM, które są zawsze pochodnymi `IDispatch` i przyjmować i zwracać określonych typów danych o nazwie typy automatyzacji. Można zautomatyzować dowolny obiekt, który udostępnia interfejsem automatyzacji udostępnia metody i właściwości, do których masz dostęp z innych aplikacji. Automatyzacja jest dostępna dla obiektów COM i OLE. Automatyczne obiektu może być lokalnym lub zdalnym (na innym komputerze dostępny w sieci); Dlatego istnieją dwie kategorie automatyzacji:  
  
-   Automatyzacja (lokalne).  
  
-   [Automatyzacja zdalna](../mfc/remote-automation.md) (za pośrednictwem sieci przy użyciu rozproszonego modelu COM lub DCOM).  
  
 Udostępnianie obiektów jest przydatne, gdy aplikacje zapewniać funkcje przydatne do innych aplikacji. Na przykład formant ActiveX jest typem serwera automatyzacji. hosting kontrolki ActiveX aplikacji jest klient automatyzacji tego formantu.  
  
 Inny przykład edytor tekstów może narazić jego działanie sprawdzania pisowni do innych programów. Narażenia obiektów umożliwia dostawcom zwiększyć swoje aplikacje za pomocą funkcji gotowe do użycia z innych aplikacji. W ten sposób automatyzacji zastosowanie niektórych zasad programowanie zorientowane obiektowo, takie jak możliwość ponownego wykorzystania i hermetyzacji na poziomie same aplikacje.  
  
 Większe znaczenie jest obsługa automatyzacji zapewnia użytkownikom i dostawców rozwiązań. W przypadku wystawianego funkcjonalność aplikacji za pośrednictwem wspólnego interfejsu dobrze zdefiniowany, automatyzacji umożliwia kompleksowe rozwiązania w jednym ogólne język programowania, takich jak Microsoft Visual Basic, zamiast w różnych kompilacji języki makro specyficzne dla aplikacji.  
  
 Wiele aplikacji komercyjnych, takich jak program Microsoft Excel i Microsoft Visual C++ pozwalają automatycznie wykonuje sporą część ich funkcji. Na przykład w programie Visual C++, możesz zapisać, makra skrypt VBScript w celu zautomatyzowania kompilacje aspektów kodu, edytowanie i debugowanie zadań.  
  
##  <a name="_core_passing_parameters_in_automation"></a>Przekazywanie parametrów w automatyzacji  
 Kłopotliwe w tworzeniu metod automatyzacji pomaga mechanizm uniform "bezpiecznej" do przekazywania danych między serwerami automatyzacji i klientami. Używa automatyzacji **VARIANT** typu do przekazywania danych. **VARIANT** typ jest oznakowany union. Ma element członkowski danych dla wartości (jest to anonimowa Unia C++) i wskazujący typ informacji przechowywanych w Unii elementu członkowskiego danych. **VARIANT** typu obsługuje wiele typów danych standardowe: 2 i 4-bajtowych liczb całkowitych, 4 i 8-bajtowych liczb zmiennoprzecinkowych, ciągi i wartościami logicznymi. Ponadto obsługuje `HRESULT` (kody błędów OLE), **waluty** (stałoprzecinkowe typ liczbowy), i **data** typy (bezwzględne datę i godzinę), oraz wskaźniki do **IUnknown**  i `IDispatch` interfejsów.  
  
 **VARIANT** typu jest hermetyzowany w [COleVariant](../mfc/reference/colevariant-class.md) klasy. Obsługa **waluty** i **data** klasy znajdują się w [COleCurrency](../mfc/reference/colecurrency-class.md) i [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) klasy.  
  
## <a name="automation-samples"></a>Przykłady automatyzacji  
  
-   [Aplikacji AUTOCLIK](../visual-cpp-samples.md) użyć tego przykładu, aby dowiedzieć się więcej techniki automatyzacji i jako podstawę do uczenia automatyzacji zdalnej.  
  
-   [Acdual —](../visual-cpp-samples.md) dodaje dwa interfejsy do automatyzacji aplikacji serwera.  
  
-   [CALCDRIV](../visual-cpp-samples.md) zwiększają MFCCALC aplikacji klienckiej automatyzacji.  
  
-   [INPROC](../visual-cpp-samples.md) pokazuje automatyzacji procesu w aplikacji serwera.  
  
-   [IPDRIVE](../visual-cpp-samples.md) zwiększają INPROC aplikacji klienckiej automatyzacji.  
  
-   [MFCCALC](../visual-cpp-samples.md) przedstawiono aplikację klienta automatyzacji.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Klienci automatyzacji](../mfc/automation-clients.md)  
  
-   [Serwery automatyzacji](../mfc/automation-servers.md)  
  
-   [Automatyzacja zdalna](../mfc/remote-automation.md)  
  
-   [OLE](../mfc/ole-in-mfc.md)  
  
-   [Technologia Active](../mfc/mfc-com.md)  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić  
  
-   [Dodawanie klasy automatyzacji](../mfc/automation-servers.md)  
  
-   [Użyj biblioteki typów](../mfc/automation-clients-using-type-libraries.md)  
   
-   [Serwery automatyzacji dostępu](../mfc/automation-servers.md)  
  
-   [Pisanie w języku C++ klienci automatyzacji](../mfc/automation-clients.md)  
  
## <a name="see-also"></a>Zobacz też  
 [MFC COM](../mfc/mfc-com.md)
