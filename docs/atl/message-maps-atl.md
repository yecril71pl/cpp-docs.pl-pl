---
title: Komunikat map (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eaef52363ebdd79a1efb1e2e26bce016500cb722
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="message-maps-atl"></a>Mapy komunikatów (ALT)
Mapy komunikatów kojarzy funkcji obsługi z danego komunikatu, polecenia lub powiadomień. Za pomocą biblioteki ATL dla [makra mapy komunikatów](../atl/reference/message-map-macros-atl.md), można określić mapy komunikatów dla okna. Procedury okna w `CWindowImpl`, `CDialogImpl`, i `CContainedWindowT` bezpośrednie komunikatów okien jego mapę komunikatów.  
  
 [Funkcji obsługi komunikatów](../atl/message-handler-functions.md) zaakceptować dodatkowe argumentu typu `BOOL&`. Ten argument wskazuje, czy wiadomość została przetworzona i ma ustawioną wartość `TRUE` domyślnie. Funkcji obsługi można następnie ustawić argument `FALSE` aby wskazać, że nie ma obsługi wiadomości. W takim przypadku ATL będzie wyglądać dla funkcji obsługi dalsze w mapie komunikatów. Przez ustawienie tego argumentu `FALSE`, można najpierw wykonać kilka akcji w odpowiedzi na wiadomość, a następnie pozwól przetwarzania domyślne lub innej funkcji obsługi na zakończenie obsługi wiadomości.  
  
## <a name="chained-message-maps"></a>Mapy komunikatów łańcuchowa  
 ATL umożliwia łańcuch mapy komunikatów, kierującą Obsługa do mapy komunikatów zdefiniowana w klasie innej komunikatów. Na przykład można zaimplementować typowe Obsługa komunikatów w osobnej klasy zapewniające jednolite dla wszystkich okien łańcucha do tej klasy. Do klasy podstawowej lub element członkowski danych klasy mogą być powiązane.  
  
 ATL obsługuje również dynamiczne tworzenie łańcucha programów, co pozwala łańcucha do innego obiektu mapy wiadomości w czasie wykonywania. Aby zaimplementować dynamiczne tworzenie łańcucha programów, musi pochodzić z klasy [CDynamicChain](../atl/reference/cdynamicchain-class.md). Następnie zadeklarować [CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) makra mapy wiadomości. `CHAIN_MSG_MAP_DYNAMIC` wymaga unikatowy numer identyfikujący obiekt i mapy komunikatów, do którego łańcucha. Należy określić to unikatowa wartość poprzez wywołanie `CDynamicChain::SetChainEntry`.  
  
 Tworzenia łańcucha dla każdej klasy, która deklaruje mapy komunikatów, pod warunkiem pochodną klasy [CMessageMap](../atl/reference/cmessagemap-class.md). `CMessageMap` Umożliwia obiektu do udostępnienia jej mapy wiadomości do innych obiektów. Należy pamiętać, że `CWindowImpl` już pochodną `CMessageMap`.  
  
## <a name="alternate-message-maps"></a>Mapy komunikatów alternatywnej  
 Na koniec ATL obsługuje mapy komunikatów alternatywne, zadeklarowana z [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) makra. Każdy mapy komunikatów alternatywny jest identyfikowany przez unikatowy numer przekazać do `ALT_MSG_MAP`. Za pomocą alternatywnej komunikatu mapy, może obsługiwać komunikaty wiele okien w jedną mapę. Należy pamiętać, że domyślnie `CWindowImpl` nie korzysta z mapy komunikatów alternatywny. Aby dodać tę obsługę, Przesłoń `WindowProc` metody w Twojej `CWindowImpl`-pochodzi z klasy i wywołanie `ProcessWindowMessage` z identyfikatorem mapy wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie okna](../atl/implementing-a-window.md)

