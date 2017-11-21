---
title: Walidacja danych okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 58fbff4a5192d15a60cf3340ce762574947fb249
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="dialog-data-validation"></a>Walidacja danych okna dialogowego
Można określić weryfikacji oprócz wymiany danych przez wywołanie funkcji DDV, jak pokazano w przykładzie w [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md). `DDV_MaxChars` Wywołania w tym przykładzie weryfikuje ciąg wprowadzony w formancie pole tekstowe nie jest dłuższa niż 20 znaków. Funkcja DDV zwykle alerty użytkownikowi okno komunikatu, jeśli sprawdzanie poprawności nie powiedzie się i umieszcza fokus na ataku kontroli, użytkownik może ponownie wprowadzić dane. Funkcja DDV określonej kontrolki musi zostać wywołany natychmiast po funkcji DDX dla tej samej kontrolki.  
  
 Można również definiować własne, niestandardowe procedury DDX i DDV. Aby uzyskać więcej informacji na ten temat oraz innych aspektów DDX i DDV, zobacz [MFC techniczne Uwaga 26](../mfc/tn026-ddx-and-ddv-routines.md).  
  
 [Dodaj kreatora zmiennej elementu członkowskiego](../ide/add-member-variable-wizard.md) spowoduje zapisanie wszystkich DDX i DDV odwołuje się mapowanie danych dla Ciebie.  
  
## <a name="see-also"></a>Zobacz też  
 [Dane okna dialogowego wymiana i Walidacja](../mfc/dialog-data-exchange-and-validation.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)   
 [Wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md)

