---
title: Wymagania kontrolek standardowych systemu Windows Vista dotyczące kompilacji
ms.date: 11/04/2016
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: c9a01665339c28b58a5d528cbb9dfaa235e7f1ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637076"
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Wymagania kontrolek standardowych systemu Windows Vista dotyczące kompilacji

Biblioteka Microsoft Foundation Class (MFC) obsługuje wspólnych formantów Windows w wersji 6.1. Formanty standardowe są uwzględnione w Windows Vista i biblioteki znajduje się w Visual Studio SDK. Biblioteka zawiera nowe metody, które podnoszą istniejących klas i nowe klasy i metody, które obsługują wspólnych formantów Windows Vista. W przypadku tworzenia aplikacji, należy przestrzegać wymagań kompilacji i migracji, które są opisane w poniższych sekcjach.

## <a name="compilation-requirements"></a>Wymagania dotyczące kompilacji

### <a name="supported-versions"></a>Obsługiwane wersje

Niektóre nowe klasy i metody obsługują tylko Windows Vista i później, podczas gdy inne metody obsługują także starszych systemów operacyjnych. Zanotuj w `Requirements` części każdego tematu Metoda określa, kiedy minimalny wymagany system operacyjny to Windows Vista.

Nawet wtedy, gdy komputer nie uruchamia się Windows Vista, można utworzyć aplikację MFC, który będzie uruchomiony na Windows Vista, jeśli masz plikach nagłówkowych MFC w wersji 6.1 na komputerze. Jednak wspólnych formantów, które są przeznaczone specjalnie dla Windows Vista działają tylko w tym systemie i są ignorowane przez starszych systemów operacyjnych.

### <a name="supported-character-sets"></a>Obsługiwanych zestawów znaków

Nowe formanty wspólne Windows obsługuje tylko zestaw znaków Unicode, a nie zestawu znaków ANSI. W przypadku tworzenia aplikacji w wierszu polecenia użyj obu następujących zdefiniuj (/ D) opcji kompilatora, aby określić Unicode jako podstawowy zestaw znaków:

```
/D_UNICODE /DUNICODE
```

Jeśli tworzysz aplikację w programie Visual Studio zintegrowane środowisko programistyczne (IDE), należy określić **zestaw znaków Unicode** opcji **zestaw znaków** właściwość **ogólne**  węzeł we właściwościach projektu.

Wersja ANSI kilka metod MFC są przestarzałe, począwszy od wersji wspólnych formantów Windows 6.1. Aby uzyskać więcej informacji, zobacz [przestarzałe interfejsy API ANSI](../mfc/deprecated-ansi-apis.md).

## <a name="migration-requirements"></a>Wymagania dotyczące migracji

Jeśli używasz programu Visual Studio IDE do tworzenia nowych aplikacji MFC, która korzysta z wersji wspólnych formantów Windows 6.1, IDE automatycznie deklaruje manifest odpowiednie. Jednak jeśli migracja istniejącej aplikacji MFC z wcześniejszej wersji programu Visual Studio, którego chcesz użyć nowe formanty wspólne środowisko IDE nie automatycznie zapewnia informacje manifestu, aby uaktualnić aplikację. Zamiast tego należy wstawić ręcznie następujące kodu źródłowego w Twojej **stdafx.h** pliku:

```
#ifdef UNICODE
#if defined _M_IX86
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_IA64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_X64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#else
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")
#endif
#endif
```

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Wykres hierarchii](../mfc/hierarchy-chart.md)<br/>
[Przestarzałe interfejsy API ANSI](../mfc/deprecated-ansi-apis.md)

