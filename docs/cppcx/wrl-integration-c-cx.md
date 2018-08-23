---
title: Integracja z WRL (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2fc36582e6ffbff8f7608a5a26cc472687132e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598093"
---
# <a name="wrl-integration-ccx"></a>Integracja z WRL (C + +/ CX)

Za darmo można łączyć WRL kodu za pomocą kodu systemu Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL). W tej samej jednostce translacji, można użyć obiektów zadeklarowanych za pomocą biblioteki WRL uchwytu do obiektu (`^`) notacją i WRL inteligentnego wskaźnika (`ComPtr<T>`) notacji. Jednak ręcznie musi obsługiwać zwracane wartości i kody błędów WRL HRESULT i wyjątków biblioteki WRL.
  
## <a name="wrl-development"></a>Tworzenie biblioteki WRL

Aby uzyskać więcej informacji na temat tworzenia i używania składników biblioteki WRL, zobacz [Windows środowiska uruchomieniowego C++ szablon biblioteki (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Przykład

Poniższy fragment kodu pokazuje i za pomocą biblioteki WRL i platformy WRL używanie klasy środowiska wykonawczego Windows w pliku metadanych.

Przykład jest pobierana z forum aplikacji Microsoft Store Tworzenie fragmentu kodu. Autor ten fragment kodu oferuje następujące zastrzeżenia i przekazanie ustalonych:

1. C++ nie zapewnia określonych interfejsów API na zastanowienie się nad typów środowiska wykonawczego Windows, ale pliki metadanych Windows (.winmd) dla typu są w pełni zgodne z plikami metadanych CLR. Windows oferuje nową wykrywania metadanych interfejsy API (RoGetMetaDataFile), aby przejść do pliku winmd dla danego typu. Jednak te interfejsy API są ograniczone zastosowanie dla deweloperów C++, ponieważ nie można utworzyć wystąpienia klasy.

1. Jest skompilowany kod, należy również przekazać Runtimeobject.lib i Rometadata.lib do konsolidatora.

1. Ten fragment kodu jest przedstawiany jako-to. Podczas gdy oczekiwano działała prawidłowo, prawdopodobnie może zawierać błędy.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}

```

## <a name="see-also"></a>Zobacz także

[Współdziałanie z innymi językami](interoperating-with-other-languages-c-cx.md)  
