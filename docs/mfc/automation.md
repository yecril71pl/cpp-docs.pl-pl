---
title: Automatyzacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e0abb9e95244b4501be96029709bc4dc412cc79
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405505"
---
# <a name="automation"></a>Automatyzacja

Automatyzacja (wcześniej znane jako automatyzacji OLE) umożliwia jedną aplikację do manipulowania obiektami implementowane w innej aplikacji lub do udostępnienia obiektów, dzięki czemu można manipulować.

[Serwer automatyzacji](../mfc/automation-servers.md) to aplikacja (typ serwera COM), która udostępnia funkcję za pośrednictwem interfejsów COM do innych aplikacji o nazwie [klientów automatyzacji](../mfc/automation-clients.md). Narażenia umożliwia klientom usługi Automation do automatyzacji niektórych funkcji przez bezpośrednie uzyskiwanie dostępu do obiektów i korzystania z usług oferowanych przez.

Serwery automatyzacji i klienci korzystają z interfejsów COM, które zawsze są uzyskiwane z `IDispatch` i przyjmują i zwracają zestaw określonych typów danych o nazwie typy automatyzacji. Można zautomatyzować dowolny obiekt, który udostępnia interfejs automatyzacji, zapewniając metody i właściwości, do których masz dostęp z innych aplikacji. Usługa Automation jest dostępna dla obiektów COM i OLE. Automatyczne obiekt może być lokalnym lub zdalnym (na innym komputerze dostępnym przez sieć); Dlatego istnieją dwie kategorie automatyzacji:

- Automatyzacja (lokalne).

- Automatyzacja zdalna (za pośrednictwem sieci przy użyciu rozproszonego modelu COM i DCOM).

Udostępnianie obiektów jest korzystne w przypadku, gdy aplikacje udostępniają funkcje przydatne do innych aplikacji. Na przykład kontrolki ActiveX jest typ serwera automatyzacji. hosting kontrolek ActiveX aplikacji jest klienta automatyzacji tej kontrolki.

Inny przykład edytora tekstów może narazić jego funkcje sprawdzania pisowni do innych programów. Narażenia obiektów umożliwia dostawcom ulepszaj swoje aplikacje za pomocą gotowych do użycia funkcji innych aplikacji. W ten sposób automatyzacji, ma zastosowanie niektórych zasad programowanie zorientowane obiektowo, takie jak możliwość ponownego wykorzystania i hermetyzacji na poziomie same aplikacje.

Niezwykle ważne jest pomocy technicznej, udostępnia automatyzacji dla użytkowników i ich dostawców rozwiązań. Dzięki uwidocznieniu działania funkcji aplikacji za pomocą interfejsu wspólny, dobrze zdefiniowanych, automatyzacji sprawia, że można tworzyć kompleksowe rozwiązania w jednym ogólne języku programowania, takich jak Microsoft Visual Basic, zamiast w różnych języki specyficzne dla aplikacji makra.

Wiele aplikacji komercyjnych, takich jak program Microsoft Excel i Microsoft Visual C++ umożliwiają zautomatyzować większość operacji ich funkcje. Na przykład w programie Visual C++, możesz napisać, makra skrypt VBScript w celu zautomatyzowania kompilacje aspekty kodu, edytowanie i debugowanie zadań.

##  <a name="_core_passing_parameters_in_automation"></a> Przekazywanie parametrów w usłudze Automation

Pomaga kłopotliwe w tworzeniu metod automatyzacji jednolitego mechanizm "bezpieczne", aby przekazać dane między klientami i serwerów usługi automation. Zastosowań automatyzacji **VARIANT** typu do przekazywania danych. **VARIANT** typem jest Unia oznakowane. Ma element członkowski danych dla wartości (jest to anonimowej Unii C++) i element członkowski danych wskazujący typ informacji przechowywanych w Unii. **VARIANT** typ obsługuje wiele typów danych w warstwie standardowa: 2 i 4-bajtowych liczb całkowitych, 4 i 8-bajtowych liczb zmiennoprzecinkowych, ciągi i wartości logiczne. Ponadto obsługuje **HRESULT** (kody błędów OLE), **waluty** (stałoprzecinkowe typu liczbowego), i **data** typów (Data bezwzględna i czas), a także wskaźniki do `IUnknown` i `IDispatch` interfejsów.

**VARIANT** typu jest hermetyzowany w [COleVariant](../mfc/reference/colevariant-class.md) klasy. Obsługa **waluty** i **data** klasy są hermetyzowane w [COleCurrency](../mfc/reference/colecurrency-class.md) i [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) klasy.

## <a name="automation-samples"></a>Przykłady automatyzacji

- [Aplikacji AUTOCLIK](../visual-cpp-samples.md) korzystać z tej próbki, Poznaj techniki automatyzacji i jako podstawa uczenia automatyzacji zdalnej.

- [Acdual —](../visual-cpp-samples.md) dodaje dwa interfejsy aplikację serwera automatyzacji.

- [CALCDRIV](../visual-cpp-samples.md) nawyki MFCCALC automatyzacji aplikacji klienta.

- [INPROC](../visual-cpp-samples.md) pokazuje aplikację serwera automatyzacji w procesie.

- [IPDRIVE](../visual-cpp-samples.md) zachęcanie INPROC automatyzacji aplikacji klienta.

- [MFCCALC](../visual-cpp-samples.md) pokazuje automatyzacji aplikacji klienta.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Klienci automatyzacji](../mfc/automation-clients.md)

- [Serwery automatyzacji](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Technologia Active](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dodaj klasę automatyzacji](../mfc/automation-servers.md)

- [Korzystaj z bibliotek typów](../mfc/automation-clients-using-type-libraries.md)

- [Serwery automatyzacji dostępu](../mfc/automation-servers.md)

- [Zapis klientów automatyzacji w języku C++](../mfc/automation-clients.md)

## <a name="see-also"></a>Zobacz też

[MFC COM](../mfc/mfc-com.md)
