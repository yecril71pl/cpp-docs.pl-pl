---
title: MAPI | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de955ecc25137f5305806ca5ba03ed15930574dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mapi"></a>MAPI
W tym artykule opisano Microsoft MAPI Messaging Application Programming Interface () dla deweloperów aplikacji klienta komunikatu. Obsługa podzbiór MAPI w klasie dostarcza MFC **CDocument** , ale nie Hermetyzowanie całego interfejsu API. Aby uzyskać więcej informacji, zobacz [Obsługa MAPI w MFC](../mfc/mapi-support-in-mfc.md).  
  
 MAPI to zestaw funkcji, które aplikacje obsługujące pocztę i poczty używać do tworzenia, modyfikowania, transfer i przechowywania wiadomości e-mail. Programiści aplikacji narzędzia, aby zdefiniować cel i zawartość wiadomości e-mail, a daje im elastyczność zarządzania nimi, przechowywane wiadomości. MAPI także wspólny interfejs, który deweloperzy aplikacji można użyć do utworzenia z włączoną obsługą poczty oraz aplikacje z obsługą poczty niezależne od podstawowej system obsługi wiadomości.  
  
 Klienci obsługi wiadomości udostępniają interfejsu do interakcji z Microsoft Windows do obsługi komunikatów systemu (WMS). Zazwyczaj współpraca obejmuje usługi żądań od dostawców zgodnych z interfejsem MAPI, takich jak magazyny wiadomości i książki adresowe.  
  
 Aby uzyskać więcej informacji na temat MAPI zobacz artykuły w przewodniku w Win32 MAPI (Messaging) zestawu Windows SDK.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Obsługa MAPI w MFC](../mfc/mapi-support-in-mfc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)   
 [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)   
 [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

