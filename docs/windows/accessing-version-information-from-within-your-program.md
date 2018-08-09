---
title: Uzyskiwanie dostępu do informacji o wersji z Twojego programu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79520523ebeda2cb0260d1bc79d0b6b35d33aa23
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646962"
---
# <a name="accessing-version-information-from-within-your-program"></a>Uzyskiwanie informacji o wersji z Twojego programu
### <a name="to-access-version-information-from-within-your-program"></a>Aby uzyskać dostęp do informacji o wersji z Twojego programu  
  
Aby uzyskać dostęp do informacji o wersji z Twojego programu, należy użyć [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) funkcji i [VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) funkcji.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor informacji o wersji](../windows/version-information-editor.md)   
 [Informacje o wersji (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)