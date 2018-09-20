---
title: Określanie lokalizacji i rozmiaru okna dialogowe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e825dc7b20c0ce75ca1f55fb9ad0310571316a1c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435821"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box-c"></a>Określanie lokalizacji i rozmiaru okna dialogowe (C++)

Lokalizacja i rozmiar, okno dialogowe C++, jak również lokalizacji i rozmiaru formantów w nim, są mierzone w jednostkach okna dialogowego. Wartości dla poszczególnych formantów i w oknie dialogowym są wyświetlane w prawej dolnej części paska po ich wybraniu stanu programu Visual Studio.

Istnieją trzy właściwości, które można ustawić w [okno właściwości](/visualstudio/ide/reference/properties-window) do określenia, gdzie zostanie wyświetlone okno dialogowe na ekranie. **Centrum** właściwość jest atrybut typu wartość logiczna; Jeśli równa wartości **True**, okno dialogowe pojawia się zawsze w środku ekranu. Jeśli ustawisz na **False**, możesz ustawić **Pozycja_x** i **Pozycja_y** właściwości umożliwia jawne zdefiniowanie w przypadku, gdy na ekranie, zostanie wyświetlone okno dialogowe. Właściwości pozycji są wartości przesunięcia z lewym górnym rogu obszaru wyświetlania, która jest zdefiniowana jako `{X=0, Y=0}`. Pozycja również opiera się na **bezwzględnie Wyrównaj** właściwości: Jeżeli **True**, współrzędne są podawane względem ekranu; Jeśli **False**, współrzędne są podawane względem okna dialogowego Okno właściciela.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)