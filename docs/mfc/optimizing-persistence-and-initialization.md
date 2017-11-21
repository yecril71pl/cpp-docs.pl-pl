---
title: "Optymalizacja stanu trwałego i inicjalizacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7b1e38a6ca424a71418790b18b3c115d12bb3065
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="optimizing-persistence-and-initialization"></a>Optymalizacja stanu trwałego i inicjalizacji
Domyślnie stanu trwałego i inicjalizacji w formancie są obsługiwane przez `DoPropExchange` funkcję elementu członkowskiego. W formancie typowe tej funkcji zawiera kilka wywołania **PX_** funkcje (`PX_Color`, `PX_Font`i tak dalej), po jednej dla każdej właściwości.  
  
 Zaletą tej metody jest który pojedynczy `DoPropExchange` implementacja może służyć do zainicjowania, trwałości w formacie binarnym i trwałości w formacie tak zwane "-zbioru właściwości" używanym przez niektóre kontenery. Ta funkcja jeden udostępnia wszystkie informacje o właściwościach i ich wartości domyślne w jednym miejscu wygodne.  
  
 Jednak ta odpisy pochodzi kosztem wydajności. **PX_** funkcje Pobierz ich elastyczność za pośrednictwem wielowarstwowe implementacji, które są z założenia mniej wydajne niż podejścia bardziej bezpośrednie, ale mniej elastyczne. Ponadto jeśli formant przekazuje wartość domyślną do **PX_** działanie, że wartość domyślna musi zapewniać zawsze, nawet w sytuacjach, gdy wartość domyślna nie musi być używana. Jeśli Generowanie wartości domyślnej jest proste zadania (na przykład, jeśli wartość jest uzyskiwany z właściwością otoczenia), a następnie dodatkowy, niepotrzebne pracy odbywa się w przypadkach, gdy nie jest używana wartość domyślna.  
  
 Formantu binarne trwałości wydajność można poprawić przez zastąpienie formantu `Serialize` funkcji. Domyślna implementacja funkcji członkowskiej nawiązuje połączenie z `DoPropExchange` funkcji. Przez zastąpienie go, musisz podać więcej bezpośredniej implementacji binarne trwałości. Rozważmy na przykład to `DoPropExchange` funkcji:  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]  
  
 Aby poprawić wydajność trwałości binarnych tego formantu, można zastąpić `Serialize` działają w następujący sposób:  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]  
  
 `dwVersion` Zmienna lokalna może służyć do wykrywania wersji trwały stan formantu jest zapisywany lub ładowany. Można użyć tej zmiennej, zamiast wywoływać metodę [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion).  
  
 Zapisanie małej ilości miejsca w trwałym formacie dla **BOOL** właściwości (i być zgodny z formatem utworzonego przez `PX_Bool`), można przechowywać właściwość jako **BAJTÓW**w następujący sposób:  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]  
  
 Zauważ, że w przypadku obciążenia zmiennej tymczasowej jest używana i następnie jego wartość jest przypisywana, zamiast rzutowanie `m_boolProp` do **BAJTÓW** odwołania. Techniki rzutowanie spowoduje tylko jednego bajtu `m_boolProp` są modyfikowane, pozostawiając Pozostała liczba bajtów, odinicjowany.  
  
 Dla tej samej kontrolki, aby zoptymalizować inicjowania formantu przez zastąpienie [COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) w następujący sposób:  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]  
  
 Mimo że `Serialize` i `OnResetState` została zastąpiona, `DoPropExchange` funkcji powinny być przechowywane bez zmian, ponieważ jest nadal używana trwałości w formacie zbioru właściwości. Należy zachować wszystkie trzy te funkcje zapewniające formantu spójnie zarządza jego właściwości, niezależnie od tego, które trwałości używa mechanizmu kontenera.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty MFC ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md)

