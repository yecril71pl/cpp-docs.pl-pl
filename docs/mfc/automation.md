---
title: Automatyzacja
ms.date: 11/04/2016
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
ms.openlocfilehash: e9320ccf7a21c6110c51366fa8af96596512a4a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370824"
---
# <a name="automation"></a>Automatyzacja

Automatyzacja (wcześniej znany jako automatyzacji OLE) umożliwia jednej aplikacji do manipulowania obiektami zaimplementowanymi w innej aplikacji lub uwidaczniać obiekty, dzięki czemu mogą być manipulowane.

[Serwer automatyzacji](../mfc/automation-servers.md) to aplikacja (typ serwera COM), która udostępnia swoje funkcje za pośrednictwem interfejsów COM innym aplikacjom o nazwie [Klienci automatyzacji](../mfc/automation-clients.md). Ekspozycja umożliwia klientom automatyzacji automatyzację niektórych funkcji poprzez bezpośredni dostęp do obiektów i korzystanie z usług, które świadczą.

Serwery automatyzacji i klienci używają interfejsów `IDispatch` COM, które są zawsze pochodne i wziąć i zwrócić określony zestaw typów danych o nazwie typy automatyzacji. Można zautomatyzować dowolny obiekt, który udostępnia interfejs automatyzacji, zapewniając metody i właściwości, które można uzyskać dostęp z innych aplikacji. Automatyzacja jest dostępna dla obiektów OLE i COM. Obiekt zautomatyzowany może być lokalny lub zdalny (na innym komputerze dostępnym w sieci); w związku z tym istnieją dwie kategorie automatyzacji:

- Automatyzacja (lokalna).

- Automatyzacja zdalna (za pośrednictwem sieci, przy użyciu rozproszonej com lub DCOM).

Uwidacznianie obiektów jest korzystne, gdy aplikacje zapewniają funkcje przydatne dla innych aplikacji. Na przykład formant ActiveX jest typem serwera automatyzacji; aplikacja hostująca formant ActiveX jest klientem automatyzacji tego formantu.

Innym przykładem edytor tekstu może narazić jego funkcje sprawdzania pisowni na inne programy. Ekspozycja obiektów umożliwia dostawcom ulepszanie swoich aplikacji przy użyciu gotowych funkcji innych aplikacji. W ten sposób automatyzacja stosuje niektóre zasady programowania obiektowego, takie jak możliwość ponownego użycia i hermetyzacja, na poziomie samych aplikacji.

Ważniejsze jest wsparcie, które automatyzacja zapewnia użytkownikom i dostawcom rozwiązań. Udostępniając funkcje aplikacji za pośrednictwem wspólnego, dobrze zdefiniowanego interfejsu, automatyzacja umożliwia tworzenie kompleksowych rozwiązań w jednym ogólnym języku programowania, takim jak Microsoft Visual Basic, zamiast w różnych językach makr specyficznych dla aplikacji.

Wiele aplikacji komercyjnych, takich jak Microsoft Excel i Microsoft Visual C++, umożliwia automatyzację wielu ich funkcji. Na przykład w języku Visual C++ można pisać makra VBScript, aby zautomatyzować kompilacje, aspekty edycji kodu lub debugowania zadań.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a>Przekazywanie parametrów w automatyzacji

Jedną z trudności w tworzeniu metod automatyzacji jest pomoc w zapewnieniu jednolitego "bezpiecznego" mechanizmu przekazywania danych między serwerami automatyzacji a klientami. Automatyzacja używa typu **VARIANT** do przekazywania danych. Typ **VARIANT** jest oznakowanym związkiem. Ma element członkowski danych dla wartości (jest to anonimowa unia C++ ) i element członkowski danych wskazujący typ informacji przechowywanych w unii. Typ **VARIANT** obsługuje szereg standardowych typów danych: 2- i 4-bajtowe liczby całkowite, 4- i 8-bajtowe liczby zmiennoprzecinkowe, ciągi i wartości logiczne. Ponadto obsługuje typy **HRESULT** (ole error codes), **CURRENCY** (typ numeryczny o stałym punkcie) i **DATE** (data `IUnknown` `IDispatch` bezwzględna i godzina), a także wskaźniki do i interfejsów.

Typ **VARIANT** jest hermetyzowany w [klasie COleVariant.](../mfc/reference/colevariant-class.md) Obsługuje **currency** i **date** klasy są hermetyzowane w [COleCurrency](../mfc/reference/colecurrency-class.md) i [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) klasy.

## <a name="automation-samples"></a>Przykłady automatyzacji

- [AUTOCLIK (AUTOCLIK)](../overview/visual-cpp-samples.md) Użyj tego przykładu, aby nauczyć się technik automatyzacji i jako podstawa do nauki automatyzacji zdalnej.

- [ACDUAL (ACDUAL)](../overview/visual-cpp-samples.md) Dodaje dwa interfejsy do aplikacji serwera automatyzacji.

- [CALCDRIV (CALCDRIV)](../overview/visual-cpp-samples.md) Automatyzacja aplikacji klienckiej jazdy MFCCALC.

- [INPROC (INPROC)](../overview/visual-cpp-samples.md) Demonstruje aplikację serwera automatyzacji w trakcie.

- [Usługa IPDRIVE](../overview/visual-cpp-samples.md) Automatyzacja aplikacji klienckiej jazdy INPROC.

- [MfccaLC ( MFCCALC )](../overview/visual-cpp-samples.md) Demonstruje aplikację klienta automatyzacji.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Klienci automatyzacji](../mfc/automation-clients.md)

- [Serwery automatyzacji](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Aktywna technologia](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dodawanie klasy automatyzacji](../mfc/automation-servers.md)

- [Korzystanie z bibliotek tekstowych](../mfc/automation-clients-using-type-libraries.md)

- [Dostęp do serwerów automatyzacji dostępu](../mfc/automation-servers.md)

- [Zapisuj klientów automatyzacji w języku C++](../mfc/automation-clients.md)

## <a name="see-also"></a>Zobacz też

[MFC COM](../mfc/mfc-com.md)
