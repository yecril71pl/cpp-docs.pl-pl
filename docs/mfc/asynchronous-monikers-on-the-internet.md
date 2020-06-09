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
ms.openlocfilehash: 74add1ad894f883c67eefab888898c0abf518b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625032"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Minikery asynchroniczne w Internecie

Internet wymaga nowych metod projektowania aplikacji z powodu wolnego dostępu do sieci. Aplikacje powinny wykonywać dostęp do sieci asynchronicznie, aby uniknąć wstrzymania interfejsu użytkownika. Klasa MFC [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) zapewnia asynchroniczną obsługę pobierania plików.

Za pomocą monikerów asynchronicznych można rozłożyć aplikację COM, aby była pobierana asynchronicznie przez Internet i zapewnić stopniowe renderowanie dużych obiektów, takich jak mapy bitowe i obiekty VRML. Monikery asynchroniczne umożliwiają pobranie właściwości kontrolki ActiveX lub pliku z Internetu bez blokowania odpowiedzi interfejsu użytkownika.

## <a name="advantages-of-asynchronous-monikers"></a>Zalety asynchronicznych monikerów

Monikery asynchroniczne można używać do:

- Pobierz kod i pliki bez blokowania.

- Pobieranie właściwości w kontrolkach ActiveX bez blokowania.

- Otrzymuj powiadomienia o postępie pobierania.

- Śledź informacje o postępie i stanie gotowości.

- Podaj informacje o stanie dla użytkownika dotyczące postępu.

- Zezwalaj użytkownikowi na anulowanie pobierania w dowolnym momencie.

## <a name="mfc-classes-for-asynchronous-monikers"></a>Klasy MFC dla monikerów asynchronicznych

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md) jest wyprowadzany z [CMonikerFile](reference/cmonikerfile-class.md), który z kolei jest wyprowadzany z [COleStreamFile](reference/colestreamfile-class.md). `COleStreamFile`Obiekt reprezentuje strumień danych; `CMonikerFile` obiekt używa `IMoniker` do uzyskania danych, a `CAsyncMonikerFile` obiekt robi to asynchronicznie.

Monikery asynchroniczne są używane przede wszystkim w aplikacjach internetowych i kontrolkach ActiveX w celu zapewnienia, że interfejs użytkownika odpowiada podczas transferu plików. Przykładem jest użycie [CDataPathProperty](reference/cdatapathproperty-class.md) do dostarczania właściwości asynchronicznych dla formantów ActiveX.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>Klasy MFC dla ścieżek danych w kontrolkach ActiveX

Klasy MFC `CDataPathProperty` i [CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md) implementują właściwości kontrolki ActiveX, które mogą być ładowane asynchronicznie. Właściwości asynchroniczne są ładowane po asynchronicznym inicjacji. Asynchroniczne kontrolki ActiveX powtarzają wywołania zwrotne w celu wskazania dostępności nowych danych podczas długotrwałego procesu wymiany właściwości.

`CDataPathProperty`pochodzi od `CAsyncMonikerFile` . `CCachedDataPathProperty`pochodzi od `CDataPathProperty` . Aby zaimplementować właściwości asynchroniczne w formantach ActiveX, Utwórz klasę z `CDataPathProperty` lub `CCachedDataPathProperty` i Zastąp [OnDataAvailable](reference/casyncmonikerfile-class.md#ondataavailable) i inne powiadomienia, które chcesz otrzymywać.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Aby pobrać plik przy użyciu monikerów asynchronicznych

1. Zadeklaruj klasę pochodną [CAsyncMonikerFile](reference/casyncmonikerfile-class.md).

1. Zastąp [OnDataAvailable](reference/casyncmonikerfile-class.md#ondataavailable) , aby wyświetlić dane.

1. Przesłoń inne funkcje członkowskie, w tym [OnProgress](reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](reference/casyncmonikerfile-class.md#onstartbinding)i [OnStopBinding](reference/casyncmonikerfile-class.md#onstopbinding).

1. Zadeklaruj wystąpienie tej klasy i użyj go do otwarcia adresów URL.

Aby uzyskać informacje o asynchronicznym pobieraniu w kontrolce ActiveX, zobacz [kontrolki ActiveX w Internecie](activex-controls-on-the-internet.md).

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](mfc-internet-programming-basics.md)
