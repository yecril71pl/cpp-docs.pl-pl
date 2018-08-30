---
title: Modyfikowanie symboli WINVER i _WIN32_WINNT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/04/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WINVER in an upgraded Visual C++ project
- _WIN32_WINNT in an upgraded Visual C++ project
ms.assetid: 6a1f1d66-ae0e-48a7-81c3-524d8e8f3447
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6593168e87f8a0dde1dd996aeadf2d225adbbe72
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194182"
---
# <a name="modifying-winver-and-win32winnt"></a>Modyfikowanie symboli WINVER i _WIN32_WINNT

Visual C++ nie obsługuje już określania wartości docelowej Windows 95, Windows 98, Windows ME, Windows NT lub Windows 2000. Jeśli Twoje **WINVER** lub **_WIN32_WINNT** makra są przypisane do jednej z tych wersji systemu Windows, należy zmodyfikować makra. Kiedy uaktualniasz projekt, który został utworzony przy użyciu wcześniejszej wersji programu Visual C++, mogą pojawić się błędy kompilacji związane z **WINVER** lub **_WIN32_WINNT** makra, jeśli przypisano do wersji Windows, który nie jest już obsługiwana.  
  
## <a name="remarks"></a>Uwagi  

Aby zmodyfikować makra, w pliku nagłówkowym (na przykład targetver.h znajdującą się po utworzeniu projektu, który jest przeznaczony dla Windows), Dodaj następujące wiersze.  
  
```C  
#define WINVER 0x0A00  
#define _WIN32_WINNT 0x0A00  
```  
  
Jest przeznaczony dla systemu operacyjnego Windows 10. Te wartości są wymienione w pliku nagłówkowym Windows nagłówka SDKDDKVer.h, który definiuje również makra dla każdej wersji Windows. Należy dodać #define wyrażenie przed dołączeniem nagłówka SDKDDKVer.h. Poniżej przedstawiono wiersze z wersji systemu Windows 10 nagłówka SDKDDKVer.h zakodować wartości dla każdej wersji systemu Windows:  
  
```C  
//  
// _WIN32_WINNT version constants  
//  
#define _WIN32_WINNT_NT4                    0x0400 // Windows NT 4.0  
#define _WIN32_WINNT_WIN2K                  0x0500 // Windows 2000  
#define _WIN32_WINNT_WINXP                  0x0501 // Windows XP  
#define _WIN32_WINNT_WS03                   0x0502 // Windows Server 2003  
#define _WIN32_WINNT_WIN6                   0x0600 // Windows Vista  
#define _WIN32_WINNT_VISTA                  0x0600 // Windows Vista  
#define _WIN32_WINNT_WS08                   0x0600 // Windows Server 2008  
#define _WIN32_WINNT_LONGHORN               0x0600 // Windows Vista  
#define _WIN32_WINNT_WIN7                   0x0601 // Windows 7  
#define _WIN32_WINNT_WIN8                   0x0602 // Windows 8  
#define _WIN32_WINNT_WINBLUE                0x0603 // Windows 8.1  
#define _WIN32_WINNT_WINTHRESHOLD           0x0A00 // Windows 10  
#define _WIN32_WINNT_WIN10                  0x0A00 // Windows 10  
```  
  
Jeśli nie widzisz wszystkich tych wersjach systemu Windows wymienionych w kopię nagłówka SDKDDKVer.h, który widzisz, prawdopodobnie używasz starszej wersji zestawu Windows SDK. Domyślnie projekty Win32 w programie Visual Studio 2017, użyj zestawu SDK systemu Windows 10.   
  
> [!NOTE]
> Wartości nie musi działać, jeśli obejmują wewnętrzny nagłówki MFC w aplikacji.  
  
Można również zdefiniować to makro za pomocą `/D` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md).  
  
Aby uzyskać więcej informacji na temat znaczenia tych makr, zobacz [przy użyciu nagłówków Windows](/windows/desktop/WinProg/using-the-windows-headers).  
  
## <a name="see-also"></a>Zobacz też  

[Historia zmian Visual C++](..\porting\visual-cpp-change-history-2003-2015.md)