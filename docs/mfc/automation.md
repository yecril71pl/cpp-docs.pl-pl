---
title: Automation
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
ms.openlocfilehash: e5790be14f26f59c2b51b339c8bee7c5eca7d692
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616514"
---
# <a name="automation"></a>Automation

Automatyzacja (dawniej znana jako Automatyzacja OLE) umożliwia jednej aplikacji manipulowanie obiektami zaimplementowanymi w innej aplikacji lub Uwidacznianie obiektów, aby można było manipulować nimi.

[Serwer automatyzacji](automation-servers.md) to aplikacja (typ serwera com), która udostępnia swoje funkcje za pomocą interfejsów com do innych aplikacji nazywanych [klientami automatyzacji](automation-clients.md). Ekspozycja umożliwia klientom automatyzacji Automatyzowanie niektórych funkcji przez bezpośrednie uzyskiwanie dostępu do obiektów i korzystanie z udostępnianych przez nich usług.

Serwery i klienci automatyzacji używają interfejsów COM, które są zawsze wyprowadzane z `IDispatch` i pobierają i zwracają określony zestaw typów danych o nazwie typy automatyzacji. Można zautomatyzować każdy obiekt, który uwidacznia interfejs automatyzacji, dostarczając metody i właściwości, do których można uzyskać dostęp z innych aplikacji. Automatyzacja jest dostępna zarówno dla obiektów OLE, jak i COM. Zautomatyzowany obiekt może być lokalny lub zdalny (na innym komputerze dostępnym w sieci); w związku z tym istnieją dwie kategorie automatyzacji:

- Automatyzacja (lokalna).

- Automatyzacja zdalna (za pośrednictwem sieci, przy użyciu rozproszonego modelu COM lub modelu DCOM).

Udostępnianie obiektów jest korzystne, gdy aplikacje zapewniają funkcje przydatne dla innych aplikacji. Na przykład Kontrolka ActiveX jest typem serwera automatyzacji; Aplikacja hostującym formant ActiveX jest klientem automatyzacji tej kontrolki.

Innym przykładem może być możliwość sprawdzania pisowni przez procesor tekstów w innych programach. Narażenie obiektów umożliwia dostawcom ulepszanie aplikacji przy użyciu gotowych funkcji innych aplikacji. W ten sposób Automatyzacja stosuje niektóre zasady programowania zorientowanego obiektowo, takie jak ponowne wykorzystywanie i hermetyzacja, na poziomie aplikacji.

Ważniejsze jest Automatyzacja pomocy technicznej dla użytkowników i dostawców rozwiązań. Dzięki wykorzystaniu funkcji aplikacji za pomocą wspólnego, dobrze zdefiniowanego interfejsu Automatyzacja zapewnia możliwość tworzenia kompleksowych rozwiązań w jednym ogólnym języku programowania, takim jak Microsoft Visual Basic, a nie w różnych językach makr specyficznych dla aplikacji.

Wiele aplikacji komercyjnych, takich jak program Microsoft Excel i Microsoft Visual C++, umożliwia automatyzację wielu funkcji. Na przykład w Visual C++ można napisać makra VBScript do automatyzowania kompilacji, aspektów edytowania kodu lub debugowania zadań.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a>Przekazywanie parametrów w usłudze Automation

Jedną z trudności w tworzeniu metod automatyzacji jest pomoc w zapewnianiu jednolitego "bezpiecznego" mechanizmu przekazywania danych między serwerami automatyzacji i klientami. Automatyzacja używa typu **wariantu** do przekazywania danych. Typ **Variant** jest oznaczonym Unią. Ma element członkowski danych dla wartości (jest to anonimowa Unia C++) i element członkowski danych wskazujący typ informacji przechowywanych w związku. Typ **Variant** obsługuje wiele standardowych typów danych: 2-i 4-bajtowe liczby całkowite, liczby zmiennoprzecinkowe 4-i 8-bajtowe, ciągi i wartości logiczne. Ponadto obsługuje wartość **HRESULT** (kod błędu OLE), **walutę** (typ liczbowy stałego punktu) i **datę** (bezwzględną datę i godzinę), a także wskaźniki do `IUnknown` i `IDispatch` interfejsy.

Typ **Variant** jest hermetyzowany w klasie [COleVariant](reference/colevariant-class.md) . Klasy z pomocniczą **walutą** i **datą** są hermetyzowane w klasach [COleCurrency](reference/colecurrency-class.md) i [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) .

## <a name="automation-samples"></a>Przykłady automatyzacji

- [Aplikacji AUTOCLIK](../overview/visual-cpp-samples.md) Użyj tego przykładu, aby poznać techniki automatyzacji i podstawę do uczenia się zdalnej automatyzacji.

- [ACDUAL](../overview/visual-cpp-samples.md) Dodaje dwa interfejsy do aplikacji serwera automatyzacji.

- [CALCDRIV](../overview/visual-cpp-samples.md) Aplikacja kliencka usługi Automation MFCCALC.

- [Procedura INproc](../overview/visual-cpp-samples.md) Demonstruje aplikację serwera automatyzacji w procesie.

- [IPDRIVE](../overview/visual-cpp-samples.md) Obsługa klienta usługi Automation.

- [MFCCALC](../overview/visual-cpp-samples.md) Demonstruje aplikację kliencką usługi Automation.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Klienci automatyzacji](automation-clients.md)

- [Serwery automatyzacji](automation-servers.md)

- [OLE](ole-in-mfc.md)

- [Technologia Active](mfc-com.md)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dodaj klasę automatyzacji](automation-servers.md)

- [Użyj bibliotek typów](automation-clients-using-type-libraries.md)

- [Dostęp do serwerów automatyzacji](automation-servers.md)

- [Pisanie klientów automatyzacji w języku C++](automation-clients.md)

## <a name="see-also"></a>Zobacz też

[MFC COM](mfc-com.md)
