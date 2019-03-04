---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: a5f60e1ba8c2b68ddca312859694f532e38da965
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279110"
---
# <a name="mapi"></a>MAPI

W tym artykule opisano Microsoft Application Programming Interface MAPI (Messaging) dla deweloperów aplikacji wiadomość klienta. MFC dostarcza obsługę podzbiór MAPI w klasie `CDocument` , ale nie hermetyzuje całego interfejsu API. Aby uzyskać więcej informacji, zobacz [Obsługa MAPI w MFC](../mfc/mapi-support-in-mfc.md).

MAPI to zestaw funkcji, których aplikacje obsługujące pocztę i obsługujących wiadomości e-mail do tworzenia, modyfikowania, transfer i przechowywać wiadomości pocztowe. On daje deweloperom aplikacji narzędzia, aby zdefiniować cel i zawartość wiadomości e-mail i umożliwia im elastyczność zarządzania nimi, wiadomości e-mail przechowywanych. MAPI udostępnia wspólny interfejs, który deweloperzy aplikacji można użyć do utworzenia z włączoną obsługą poczty i aplikacje z obsługą wiadomości e-mail niezależnie od zasadniczego systemu obsługi komunikatów.

Klienci obsługi wiadomości zapewnić ludzi interfejs do interakcji z Microsoft Windows Messaging System (WMS). Ta interakcja obejmują zazwyczaj żądania usług z CLS MAPI dostawców, takich jak magazyny wiadomości i książek adresowych.

Aby uzyskać więcej informacji na temat interfejsu MAPI zobacz artykuły w przewodniku w Win32 MAPI (Messaging) zestawu Windows SDK.

## <a name="in-this-section"></a>W tej sekcji

[Obsługa MAPI w MFC](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>Zobacz także

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)
