---
title: Zabezpieczenia w automatyzacji zdalnej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AllowRemoteActivation [MFC]
- Remote Automation [MFC], security
- activating objects [MFC]
- security [MFC]
- Automation objects [MFC], security options
- object activation [MFC]
- security [MFC], Remote Automation
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e535fac6330d6268629e8e3681fec47c7b0d65d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="security-in-remote-automation"></a>Zabezpieczenia w automatyzacji zdalnej
Automatyzacja zdalna obsługuje podstawowy poziom zabezpieczeń, aby umożliwić moduł zapisujący aplikacji serwera (lub, zamiast jego administratora) określ, jak określony obiekt może zdalnie. Wszystkie obiekty automatyzacji w danym systemie mogą ustawiać globalnie "nie zezwalaj na aktywację zdalną" lub "zezwolenia na aktywację zdalną". Ponadto i częściej pojedyncze obiekty mogą mieć takiej możliwości. Automatyzacja zdalna jest stosowany klucz w rejestrze każdego obiektu, **AllowRemoteActivation**, aby ustalić, czy dany serwer może zdalnie aktywowane. Jeśli ustawienia ogólnosystemowe tego trybu należy używać, następnie każdego obiektu w rejestrze można przypisać ten klucz i poszczególnych stan każdego z nich może być równa "yes" lub "nie", zależnie od potrzeb.  
  
 Jeśli serwer w systemie Windows NT lub Windows 2000, alternatywny zabezpieczeń jest dozwolone. W takim przypadku automatyzacji zdalnej używa NT listy kontroli dostępu (ACL), aby określić, którzy użytkownicy lub grupy lub grup użytkowników mogą zdalnie aktywować danego serwera.  
  
 Należy pamiętać, że opcje zabezpieczeń są stosowane do całego obiektu. nie jest możliwe można ustawić atrybutów określonego interfejsu, lub indywidualne właściwości lub metody dla tego obiektu.  
  
 Wszystkie opcje zabezpieczeń mogą zostać ustawione za pośrednictwem Menedżera połączeń automatyzacji zdalnej (RAC).  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyzacja zdalna](../mfc/remote-automation.md)

