---
title: Dopasowanie grup formantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], aligning
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fac1c04f51b2e05213223ca3e20e4a4fcc3e54e3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651811"
---
# <a name="aligning-groups-of-controls"></a>Dopasowanie grup formantów
Poniższa procedura pokazuje, jak dopasowanie grup formantów.  
  
### <a name="to-align-groups-of-controls"></a>Dopasowanie grup formantów  
  
1.  [Zaznacz formanty](../windows/selecting-multiple-controls.md) pożądane dopasowanie. Pamiętaj o wybraniu formantu, który ma być formantu dominującego najpierw lub ustaw go jako formant dominujący przed przystąpieniem do wykonywania wyrównanie lub zmiany rozmiaru polecenia.  
  
     Ostateczne stanowisko grupy formantów, zależy od położenie formantu dominującego. Aby uzyskać więcej informacji dotyczących zaznaczania formantu dominującego zobacz [Określanie formantu dominującego](../windows/specifying-the-dominant-control.md).  
  
2.  Z **Format** menu, wybierz **Wyrównaj**, a następnie wybierz jedną z następujących wyrównanie:  
  
    -   `Lefts`: wyrównuje wybranych kontrolek wzdłuż ich po lewej stronie.  
  
    -   `Centers`: wyrównuje wybranych kontrolek w poziomie wzdłuż ich punkty Centrum.  
  
    -   `Rights`: wyrównuje wybranych kontrolek wzdłuż jego prawej stronie.  
  
    -   `Tops`: wyrównuje wybranych kontrolek wzdłuż górnej krawędzi.  
  
    -   `Middles`: wyrównuje wybranych kontrolek w pionie wzdłuż punktom środkowej.  
  
    -   `Bottoms`: wyrównuje wybranych kontrolek wzdłuż dolnej krawędzi.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Rozmieszczenie kontrolek w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)