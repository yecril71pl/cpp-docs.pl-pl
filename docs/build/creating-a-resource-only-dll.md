---
title: Tworzenie biblioteki DLL tylko z zasobami | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd65085c9a0ecc0479c7d22feb5587d1e94447de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-resource-only-dll"></a>Tworzenie biblioteki DLL z samymi zasobami  
  
Biblioteki DLL tylko z zasobami jest bibliotekę DLL, która zawiera jednak zasoby, takie jak ikony, mapy bitowe, ciągi i oknach dialogowych. Za pomocą biblioteki DLL tylko z zasobami jest dobry sposób na współużytkowanie tego samego zestawu zasobów między wiele programów. Istnieje również sposób zapewnić aplikacji zasoby zlokalizowane dla wielu języków (zobacz [zlokalizowanych zasobów w aplikacjach MFC: satelitarne biblioteki dll](../build/localized-resources-in-mfc-applications-satellite-dlls.md)).  
  
Aby utworzyć biblioteki DLL tylko z zasobami, Utwórz nowy projekt Win32 DLL (z systemem innym niż MFC) i Dodaj zasoby do projektu.  
  
-   Wybierz projekt Win32 w **nowy projekt** okna dialogowego i określić typ projektu biblioteki DLL w Kreatorze projektu Win32.  
  
-   Utwórz nowy skrypt zasobu, który zawiera zasoby (na przykład ciąg lub menu) biblioteki dll i Zapisz plik .rc.  
  
-   Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**, a następnie Włóż nowy plik .rc do projektu.  
  
-   Określ [/noentry](../build/reference/noentry-no-entry-point.md) — opcja konsolidatora. / NOENTRY Zapobiega łączeniu odwołania do konsolidator `_main` w bibliotece DLL; ta opcja jest wymagana do utworzenia biblioteki DLL tylko z zasobami.  
  
-   Skompiluj bibliotekę DLL.  
  
Aplikacji korzystającej z biblioteki DLL tylko z zasobami powinny wywoływać [LoadLibrary](../build/loadlibrary-and-afxloadlibrary.md) jawnie powiązać biblioteki DLL. Dostęp do zasobów, wywołaj funkcje ogólne `FindResource` i `LoadResource`, które działają na dowolny rodzaj zasobu lub wywoływanie jednego z następujących funkcji określonych zasobów:  
  
-   `FormatMessage`  
  
-   `LoadAccelerators`  
  
-   `LoadBitmap`  
  
-   `LoadCursor`  
  
-   `LoadIcon`  
  
-   `LoadMenu`  
  
-   `LoadString`  
  
Aplikacja powinna wywołać `FreeLibrary` po zakończeniu przy użyciu zasobów.  
  
## <a name="see-also"></a>Zobacz też  
  
[Praca z plikami zasobów](../windows/working-with-resource-files.md)  
[Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)