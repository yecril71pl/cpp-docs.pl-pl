---
title: Używanie formantu RichEdit 1.0 z MFC
ms.date: 11/04/2016
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
ms.openlocfilehash: 080ad995b9c7a041337d9b296d6ef8906e7f20ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468318"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Używanie formantu RichEdit 1.0 z MFC

Aby użyć kontrolki RichEdit, najpierw musisz wywołać [afxinitrichedit2 —](../mfc/reference/application-information-and-management.md#afxinitrichedit2) można załadować kontrolki 2.0 RichEdit (RICHED20. Biblioteka DLL), lub zadzwoń [afxinitrichedit —](../mfc/reference/application-information-and-management.md#afxinitrichedit) załadować starszej kontrolki RichEdit 1.0 (RICHED32. BIBLIOTEKA DLL).

Może używać bieżącego [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) klasy za pomocą starszej kontrolki RichEdit 1.0, ale `CRichEditCtrl` jest przeznaczona wyłącznie do obsługi formantu RichEdit w wersji 2.0. Większość metod będzie działać, ponieważ RichEdit 1.0 i RichEdit 2.0 są bardzo podobne, jednak należy pamiętać, że istnieją pewne różnice między kontrolkami 1.0 i 2.0, więc niektóre metody mogą nie działać prawidłowo lub nie działać w ogóle.

## <a name="requirements"></a>Wymagania

MFC

## <a name="see-also"></a>Zobacz też

[Rozwiązywanie problemów z Edytorem okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)