---
title: "Błąd krytyczny kompilatora zasobów RC1015 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1015
dev_langs: C++
helpviewer_keywords: RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 666221cf5c3e812cd856271ea97cf4966383ec20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1015"></a>Błąd krytyczny kompilatora zasobów RC1015
Otwórz nie można dołączyć pliku "filename"  
  
 Podany dołączanego pliku nie istnieje, nie można otworzyć lub nie został znaleziony.  
  
 Upewnij się, że ustawienia środowiska są prawidłowe i czy określono poprawną ścieżkę pliku. Upewnij się, że wystarczające dojścia do plików są dostępne dla kompilatora zasobów. Jeśli plik znajduje się na dysku sieciowym, upewnij się, że masz uprawnienia do otwierania pliku.  
  
 RC1015 może wystąpić, nawet jeśli dołączanego pliku znajduje się w katalogu określony jako kolejnego katalogu obejmują we właściwości konfiguracji -> Zasoby -> stronę Ogólne właściwości; Określ pełną ścieżkę do pliku dyrektywy include.  
  
 Aby uzyskać więcej informacji, zobacz artykuł bazy wiedzy Knowledge Base Q326987: RC1015 błąd podczas przy użyciu zasobów widoku Jeśli ścieżka Include jest zbyt długa.