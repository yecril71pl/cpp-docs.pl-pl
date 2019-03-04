---
title: Minikery asynchroniczne w Internecie
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: e7a7ea51bca134e965747db8aac7f8a62822c9eb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305032"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Minikery asynchroniczne w Internecie

Internet wymaga nowego podejścia do projektowania aplikacji ze względu na jego dostęp wolną sieć. Aplikacje, należy wykonać dostępu do sieci asynchronicznie, aby uniknąć wstrzymujących działanie interfejsu użytkownika. Klasy MFC [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) zapewnia obsługę asynchroniczną pobierania plików.

Z monikerów asynchronicznych można rozszerzyć aplikacji modelu COM do pobrania asynchroniczne w Internecie i zapewnienie progresywnego renderowania duże obiekty, takie jak mapy bitowe i VRML obiektów. Monikery asynchroniczne włączyć właściwość formantu ActiveX lub pliku w Internecie, które mają być pobrane bez blokowania odpowiedzi interfejsu użytkownika.

## <a name="advantages-of-asynchronous-monikers"></a>Korzyści wynikające z monikerów asynchronicznych

Możesz użyć monikerów asynchronicznych do:

- Pobierz kod i pliki bez blokowania.

- Pobierz właściwości w kontrolkach ActiveX bez blokowania.

- Odbieranie powiadomień, pobierania postępu.

- Śledzenie postępu i stanu gotowości informacji.

- Podaj informacje o stanie użytkownika dotyczące postępu.

- Zezwalaj użytkownikowi na pobieranie w dowolnym momencie anulować.

## <a name="mfc-classes-for-asynchronous-monikers"></a>Klasy MFC do monikerów asynchronicznych

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) jest tworzony na podstawie [CMonikerFile](../mfc/reference/cmonikerfile-class.md), który z kolei pochodzi od [COleStreamFile](../mfc/reference/colestreamfile-class.md). A `COleStreamFile` reprezentuje obiekt, a strumień danych; `CMonikerFile` obiektu używa `IMoniker` do uzyskania danych i `CAsyncMonikerFile` obiektu robi to tak asynchronicznie.

Monikery asynchroniczne są używane głównie w aplikacje internetowe i formantów ActiveX zapewnia interfejs użytkownika odpowiada podczas transferu plików. Głównym przykładem polega na użyciu [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) zapewnienie asynchronicznej właściwości formantów ActiveX.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>Klasy MFC do ścieżki danych w kontrolkach ActiveX

Klasy MFC `CDataPathProperty` i [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) implementuje właściwości formantu ActiveX, które może być ładowana asynchronicznie. Właściwości asynchronicznego są ładowane po rozpoczęciu synchroniczne. Formanty ActiveX asynchroniczne wielokrotnie wykona wywołanie zwrotne do wskazania dostępności nowych danych podczas procesu wymiany długich właściwości.

`CDataPathProperty` jest tworzony na podstawie `CAsyncMonikerFile`. `CCachedDataPathProperty` jest tworzony na podstawie `CDataPathProperty`. Aby zaimplementować właściwości asynchronicznego w Twoich kontrolek ActiveX, należy wyprowadzić klasę z `CDataPathProperty` lub `CCachedDataPathProperty`i zastępowania [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) i inne powiadomienia chcesz otrzymywać.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Aby pobrać plik przy użyciu monikerów asynchronicznych

1. Deklarowanie klasy pochodzącej od [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).

1. Zastąp [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) do wyświetlania danych.

1. Zastąpienie innych funkcji Członkowskich, w tym [OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding), i [OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding).

1. Zadeklaruj wystąpienie tej klasy i używać go na otwieranie adresów URL.

Aby dowiedzieć się, jak pobieranie asynchronicznie w kontrolce ActiveX, zobacz [kontrolki ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md).

## <a name="see-also"></a>Zobacz także

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)
