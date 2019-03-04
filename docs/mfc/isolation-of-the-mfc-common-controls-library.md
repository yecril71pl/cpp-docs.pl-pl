---
title: Izolacja biblioteki formantów wspólnych MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
ms.openlocfilehash: 94700f850be62404f22974a1d5e76acad711555c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278746"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>Izolacja biblioteki formantów wspólnych MFC

Biblioteki formantów wspólnych teraz jest izolowana w MFC, dzięki czemu różnych modułów (np. użytkownika biblioteki dll) do korzystają z różnych wersji biblioteki formantów wspólnych, określając wersję w swoich manifestach.

Aplikacja MFC (lub kod użytkownika wywołuje przez MFC) sprawia, że wywołania do biblioteki formantów wspólnych interfejsów API za pomocą funkcji otoki o nazwie `Afx` *FunctionName*, gdzie *FunctionName* to nazwa wspólna Formanty interfejsu API. Te funkcje otoki są definiowane w afxcomctl32.h i afxcomctl32.inl.

Możesz użyć [AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists) i [AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) makra (zdefiniowaną w afxcomctl32.h), aby ustalić, czy biblioteki formantów wspólnych implementuje niektórych interfejsów API zamiast wywoływać metodę [GetProcAddress](../build/getprocaddress.md).

Technicznie rzecz biorąc, wykonywać wywołania interfejsu API biblioteki formantów wspólnych za pośrednictwem klasy otoki `CComCtlWrapper` (zdefiniowanymi w afxcomctl32.h). `CComCtlWrapper` jest również odpowiedzialne za ładowanie i zwalnianie pliku Comctl32.dll. Stanu modułu MFC zawiera wskaźnik do wystąpienia `CComCtlWrapper`. Możesz uzyskać dostęp przy użyciu klasy otoki `afxComCtlWrapper` makra.

Należy pamiętać, że wywołanie wspólnych formantów interfejsu API z bezpośrednio (bez użycia funkcji otoki MFC) z MFC aplikacji lub użytkownika biblioteki DLL będzie działać w większości przypadków, ponieważ aplikacja MFC lub użytkownika biblioteki DLL jest powiązany z biblioteki formantów wspólnych żądane go w swoim manifeście). Jednak sam kod MFC musi używać otoki, ponieważ może wywołać kodu MFC z biblioteki DLL użytkownika, z użyciem różnych wersji biblioteki formantów wspólnych.
