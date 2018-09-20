---
title: MAPI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2ca182da3a0300604415b790c0aba138c8fd7a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439110"
---
# <a name="mapi"></a>MAPI

W tym artykule opisano Microsoft Application Programming Interface MAPI (Messaging) dla deweloperów aplikacji wiadomość klienta. MFC dostarcza obsługę podzbiór MAPI w klasie `CDocument` , ale nie hermetyzuje całego interfejsu API. Aby uzyskać więcej informacji, zobacz [Obsługa MAPI w MFC](../mfc/mapi-support-in-mfc.md).

MAPI to zestaw funkcji, których aplikacje obsługujące pocztę i obsługujących wiadomości e-mail do tworzenia, modyfikowania, transfer i przechowywać wiadomości pocztowe. On daje deweloperom aplikacji narzędzia, aby zdefiniować cel i zawartość wiadomości e-mail i umożliwia im elastyczność zarządzania nimi, wiadomości e-mail przechowywanych. MAPI udostępnia wspólny interfejs, który deweloperzy aplikacji można użyć do utworzenia z włączoną obsługą poczty i aplikacje z obsługą wiadomości e-mail niezależnie od zasadniczego systemu obsługi komunikatów.

Klienci obsługi wiadomości zapewnić ludzi interfejs do interakcji z Microsoft Windows Messaging System (WMS). Ta interakcja obejmują zazwyczaj żądania usług z CLS MAPI dostawców, takich jak magazyny wiadomości i książek adresowych.

Aby uzyskać więcej informacji na temat interfejsu MAPI zobacz artykuły w przewodniku w Win32 MAPI (Messaging) zestawu Windows SDK.

## <a name="in-this-section"></a>W tej sekcji

[Obsługa MAPI w MFC](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>Zobacz też

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

