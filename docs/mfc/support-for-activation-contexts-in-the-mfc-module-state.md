---
title: Obsługa kontekstów aktywacji w stanie modułu MFC
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: a2e5f56eeb323f1bd5f20c5920bbdbe4a658554d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306668"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Obsługa kontekstów aktywacji w stanie modułu MFC

MFC tworzy kontekst aktywacji przy użyciu zasobu manifestu, dostarczone przez użytkownika moduł. Aby uzyskać więcej informacji dotyczących tworzenia kontekstów aktywacji zobacz następujące tematy:

- [Konteksty aktywacji](/windows/desktop/SbsCs/activation-contexts)

- [Manifesty aplikacji](/windows/desktop/SbsCs/application-manifests)

- [Manifesty](/windows/desktop/SbsCs/assembly-manifests)

## <a name="remarks"></a>Uwagi

Czytając te tematy zestawu Windows SDK, należy pamiętać, że mechanizm kontekst aktywacji MFC przypomina kontekst aktywacji zestawu Windows SDK z tą różnicą, że MFC nie korzysta z interfejsu API Windows SDK aktywacji kontekstu.

Kontekst aktywacji działa w aplikacjach MFC, użytkownik bibliotek DLL i bibliotek DLL rozszerzeń MFC w następujący sposób:

- Resource ID 1 jest używana w aplikacjach MFC do swojego zasobu manifestu. W tym przypadku MFC nie tworzy kontekst aktywacji, ale używa domyślnego kontekstu aplikacji.

- Użytkownik MFC dll na użytek resource ID 2 ich zasobu manifestu. W tym miejscu MFC tworzy kontekst aktywacji dla każdej biblioteki DLL użytkownika, więc inny użytkownik bibliotek DLL, można użyć różnych wersji tej samej biblioteki (na przykład, Biblioteka formantów standardowych).

- Biblioteki DLL rozszerzeń MFC, zależy od hostingu aplikacji lub użytkownika biblioteki DLL nawiązać ich kontekstu aktywacji.

Mimo, że stan kontekst aktywacji można modyfikować przy użyciu procesu opisanego w sekcji [przy użyciu interfejsu API kontekst aktywacji](/windows/desktop/SbsCs/using-the-activation-context-api), przy użyciu mechanizmu kontekst aktywacji MFC mogą być przydatne podczas tworzenia oparte na bibliotekach DLL dodatku plug-in architektury Jeżeli nie jest proste (lub nie jest możliwe) ręcznie przełączać stan aktywacji przed i po poszczególnych wywołań dla zewnętrznej wtyczki.

Kontekst aktywacji jest tworzony w [afxwininit —](../mfc/reference/application-information-and-management.md#afxwininit). Zostanie zniszczony w `AFX_MODULE_STATE` destruktora. Uchwyt kontekstu aktywacji jest przechowywany w `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` jest opisana w [AfxGetStaticModuleState —](reference/extension-dll-macros.md#afxgetstaticmodulestate).)

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) makro aktywuje i dezaktywuje kontekstu aktywacji. `AFX_MANAGE_STATE` jest włączona dla bibliotek MFC statycznych, a także biblioteki MFC DLL MFC kodu do wykonania w kontekście właściwej aktywacji wybranych przez użytkownika pliku DLL.

## <a name="see-also"></a>Zobacz także

[Konteksty aktywacji](/windows/desktop/SbsCs/activation-contexts)<br/>
[Manifesty aplikacji](/windows/desktop/SbsCs/application-manifests)<br/>
[Manifesty](/windows/desktop/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
