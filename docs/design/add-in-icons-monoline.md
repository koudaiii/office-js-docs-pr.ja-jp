---
title: Office アドインの Monoline スタイルのアイコンガイドライン
description: ''
ms.date: 12/09/2019
localization_priority: Normal
ms.openlocfilehash: 5914e85305b58fb4ab05499141f31d69c507d279
ms.sourcegitcommit: 8c5c5a1bd3fe8b90f6253d9850e9352ed0b283ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "40816260"
---
# <a name="monoline-style-icon-guidelines-for-office-add-ins"></a><span data-ttu-id="ec7b3-102">Office アドインの Monoline スタイルのアイコンガイドライン</span><span class="sxs-lookup"><span data-stu-id="ec7b3-102">Monoline style icon guidelines for Office Add-ins</span></span>

<span data-ttu-id="ec7b3-103">Monoline style 図像は Office 365 で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-103">Monoline style iconography are used in Office 365.</span></span> <span data-ttu-id="ec7b3-104">アイコンがサブスクリプション以外の Office 2013 以降の新しいスタイルに一致するようにする場合は、「 [Office アドインの新しいスタイルのアイコンガイドライン](add-in-icons-fresh.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-104">If you would prefer that your icons match the Fresh style of non-subscription Office 2013+, see [Fresh style icon guidelines for Office Add-ins](add-in-icons-fresh.md).</span></span>

## <a name="office-monoline-visual-style"></a><span data-ttu-id="ec7b3-105">Office Monoline の視覚スタイル</span><span class="sxs-lookup"><span data-stu-id="ec7b3-105">Office Monoline visual style</span></span>

<span data-ttu-id="ec7b3-106">一貫性があり、わかりやすく、アクセス可能な図像を持つ Monoline スタイルの目的は、シンプルなビジュアルを使用して操作と機能を伝えるために、アイコンがすべてのユーザーに対してアクセス可能であること、および Windows の他の場所で使用されているものと一致するスタイルを持つことを示します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-106">The goal of the Monoline style to have consistent, clear, and accessible iconography to communicate action and features with simple visuals, ensure the icons are accessible to all users, and have a style that is consistent with those used elsewhere in Windows.</span></span>

<span data-ttu-id="ec7b3-107">次のガイドラインは、サードパーティの開発者が、既にインストールされているアイコンと一貫性のある機能のアイコンを作成することを希望しています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-107">The following guidelines are for 3rd party developers who want to create icons for features that will be consistent with the icons already present Office products.</span></span>

### <a name="design-principles"></a><span data-ttu-id="ec7b3-108">設計原則</span><span class="sxs-lookup"><span data-stu-id="ec7b3-108">Design principles</span></span>

-   <span data-ttu-id="ec7b3-109">シンプル、クリーン、クリア。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-109">Simple, clean, clear.</span></span>
-   <span data-ttu-id="ec7b3-110">必要な要素のみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-110">Contain only necessary elements.</span></span>
-   <span data-ttu-id="ec7b3-111">ウィンドウアイコンのスタイル。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-111">Inspired by Windows icon style.</span></span>
-   <span data-ttu-id="ec7b3-112">すべてのユーザーがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-112">Accessible to all users.</span></span>

#### <a name="conveying-meaning"></a><span data-ttu-id="ec7b3-113">意味を伝える</span><span class="sxs-lookup"><span data-stu-id="ec7b3-113">Conveying meaning</span></span>

-   <span data-ttu-id="ec7b3-114">ページなどの説明的な要素を使用して、メールを表すドキュメントまたはエンベロープを表します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-114">Use descriptive elements such as a page to represent a document or an envelope to represent mail.</span></span>
-   <span data-ttu-id="ec7b3-115">同じ概念を表すのと同じ要素を使用します。つまり、メールは常に、スタンプではなく封筒で表されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-115">Use the same element to represent the same concept, i.e., mail is always represented by an envelope, not a stamp.</span></span>
-   <span data-ttu-id="ec7b3-116">概念開発時にコアメタファを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-116">Use a core metaphor during concept development.</span></span>

#### <a name="reduction-of-elements"></a><span data-ttu-id="ec7b3-117">要素の削減</span><span class="sxs-lookup"><span data-stu-id="ec7b3-117">Reduction of Elements</span></span>

-   <span data-ttu-id="ec7b3-118">アイコンは、メタファに不可欠な要素のみを使用して、中心となる意味を小さくします。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-118">Reduce the icon to its core meaning, using only elements that are essential to the metaphor.</span></span>
-   <span data-ttu-id="ec7b3-119">アイコンのサイズに関係なく、アイコンの要素の数を2に制限します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-119">Limit the number of elements in an icon to two, regardless of icon size.</span></span>

#### <a name="consistency"></a><span data-ttu-id="ec7b3-120">一貫</span><span class="sxs-lookup"><span data-stu-id="ec7b3-120">Consistency</span></span>

<span data-ttu-id="ec7b3-121">アイコンのサイズ、配置、色は一貫している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-121">Sizes, arrangement, and color of icons should be consistent.</span></span>

#### <a name="styling"></a><span data-ttu-id="ec7b3-122">スタイル</span><span class="sxs-lookup"><span data-stu-id="ec7b3-122">Styling</span></span>

##### <a name="perspective"></a><span data-ttu-id="ec7b3-123">Perspective</span><span class="sxs-lookup"><span data-stu-id="ec7b3-123">Perspective</span></span>

<span data-ttu-id="ec7b3-124">既定では、Monoline アイコンは前方に向きます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-124">Monoline icons are forward-facing by default.</span></span> <span data-ttu-id="ec7b3-125">キューブなどの遠近や回転を必要とする一部の要素は許可されますが、例外は最小限に抑える必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-125">Certain elements that require perspective and/or rotation, such as a cube, are allowed, but exceptions should be kept to a minimum.</span></span>

##### <a name="embellishment"></a><span data-ttu-id="ec7b3-126">装飾記号</span><span class="sxs-lookup"><span data-stu-id="ec7b3-126">Embellishment</span></span>

<span data-ttu-id="ec7b3-127">Monoline は、完全な最小のスタイルです。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-127">Monoline is a clean minimal style.</span></span> <span data-ttu-id="ec7b3-128">すべてがフラットな色を使用しているため、グラデーション、テクスチャ、または光源がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-128">Everything uses flat color, which means there are no gradients, textures, or light sources.</span></span>

## <a name="designing"></a><span data-ttu-id="ec7b3-129">設計</span><span class="sxs-lookup"><span data-stu-id="ec7b3-129">Designing</span></span>

### <a name="sizes"></a><span data-ttu-id="ec7b3-130">フェース</span><span class="sxs-lookup"><span data-stu-id="ec7b3-130">Sizes</span></span>

<span data-ttu-id="ec7b3-131">高 DPI デバイスをサポートするには、これらのサイズで各アイコンを生成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-131">We recommend that you produce each icon in all these sizes to support high DPI devices.</span></span> <span data-ttu-id="ec7b3-132">絶対に*必要な*サイズは、100% のサイズなので、16 px、20px、および32px です。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-132">The absolutely *required* sizes are 16px, 20px, and 32px, as those are the 100% sizes.</span></span>

<span data-ttu-id="ec7b3-133">**16px、20px、24px、32px、40px、48px、64px、80px、96px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-133">**16px, 20px, 24px, 32px, 40px, 48px, 64px, 80px, 96px**</span></span>

### <a name="layout"></a><span data-ttu-id="ec7b3-134">レイアウト</span><span class="sxs-lookup"><span data-stu-id="ec7b3-134">Layout</span></span>

<span data-ttu-id="ec7b3-135">次に、修飾子付きのアイコンレイアウトの例を示します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-135">The following is an example of icon layout with a modifier.</span></span>

![修飾子を含むアイコンの例](../images/monolineicon1.png)  ![ベース、修飾子、スペース、およびカットアウトのグリッドの背景の吹き出しの同じ例。](../images/monolineicon2.png)

#### <a name="elements"></a><span data-ttu-id="ec7b3-138">要素</span><span class="sxs-lookup"><span data-stu-id="ec7b3-138">Elements</span></span>

- <span data-ttu-id="ec7b3-139">**Base**: アイコンが表す主な概念です。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-139">**Base**: The main concept that the icon represents.</span></span> <span data-ttu-id="ec7b3-140">これは通常、アイコンに必要なビジュアルだけですが、第2の要素 (修飾子) を使用して主な概念を拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-140">This is usually the only visual needed for the icon, but sometimes the main concept can be enhanced with a secondary element, a modifier.</span></span>

- <span data-ttu-id="ec7b3-141">**修飾子**ベースをオーバーレイする任意の要素。これは、通常、アクションまたはステータスを表す修飾子です。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-141">**Modifier** Any element that overlays the base; that is, a modifier that typically represents an action or a status.</span></span> <span data-ttu-id="ec7b3-142">追加、変更、または記述子として機能することによって、基本要素を変更します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-142">It modifies the base element by acting as an addition, alteration, or a descriptor.</span></span>

![ベースエリアと [修飾子] 領域があるグリッド。](../images/monolineicon3.png)

### <a name="construction"></a><span data-ttu-id="ec7b3-144">建設</span><span class="sxs-lookup"><span data-stu-id="ec7b3-144">Construction</span></span>

#### <a name="element-placement"></a><span data-ttu-id="ec7b3-145">要素の配置</span><span class="sxs-lookup"><span data-stu-id="ec7b3-145">Element placement</span></span>

<span data-ttu-id="ec7b3-146">Base 要素は、スペース内のアイコンの中央に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-146">Base elements are placed in the center of the icon within the padding.</span></span> <span data-ttu-id="ec7b3-147">中心を完全に配置できない場合は、上から右にエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-147">If it can't be placed perfectly centered, then the base should err to the top right.</span></span> <span data-ttu-id="ec7b3-148">次の例では、アイコンは完全に中央揃えになっています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-148">In the following example, the icon is perfectly centered:</span></span>

![完全に中央揃えアイコンが表示されている画像](../images/monolineicon4.png)

<span data-ttu-id="ec7b3-150">次の例では、アイコンは左に erring ます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-150">In the following example, the icon is erring to the left.</span></span>

![Errs の左に表示されるアイコンを示す画像](../images/monolineicon5.png)

<span data-ttu-id="ec7b3-152">修飾子は、ほとんどの場合、アイコンキャンバスの右下隅に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-152">Modifiers are almost always placed in the bottom right corner of the icon canvas.</span></span> <span data-ttu-id="ec7b3-153">まれに、修飾子が異なる隅に配置される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-153">In some rare cases, modifiers are placed in a different corner.</span></span> <span data-ttu-id="ec7b3-154">たとえば、底要素が右下隅の修飾子で認識されない場合は、左上隅に配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-154">For example, if the base element would be unrecognizable with the modifier in the bottom right corner, then consider placing it in the upper left corner.</span></span>

![右下に修飾子が表示されているいくつかのアイコンが表示されているイメージ。ただし、左上に修飾子が付いています。](../images/monolineicon6.png)

#### <a name="padding"></a><span data-ttu-id="ec7b3-156">Padding</span><span class="sxs-lookup"><span data-stu-id="ec7b3-156">Padding</span></span>

<span data-ttu-id="ec7b3-157">各サイズアイコンには、アイコンの周囲に指定された余白があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-157">Each size icon has a specified amount of padding around the icon.</span></span> <span data-ttu-id="ec7b3-158">Base 要素は埋め込みの範囲内に残りますが、補助線はキャンバスの端までになり、パディング---の外側がアイコンの輪郭の端まで拡張されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-158">The base element stays within the padding, but the modifier should butt up to the edge of the canvas, extending outside of the padding---to the edge of the icon border.</span></span> <span data-ttu-id="ec7b3-159">次の画像は、アイコンのサイズごとに推奨される埋め込みを示しています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-159">The following images show the recommended padding to use for each of the icon sizes.</span></span>

|<span data-ttu-id="ec7b3-160">**16px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-160">**16px**</span></span>|<span data-ttu-id="ec7b3-161">**20px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-161">**20px**</span></span>|<span data-ttu-id="ec7b3-162">**24px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-162">**24px**</span></span>|<span data-ttu-id="ec7b3-163">**32px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-163">**32px**</span></span>|<span data-ttu-id="ec7b3-164">**40px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-164">**40px**</span></span>|<span data-ttu-id="ec7b3-165">**48px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-165">**48px**</span></span>|<span data-ttu-id="ec7b3-166">**64px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-166">**64px**</span></span>|<span data-ttu-id="ec7b3-167">**80px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-167">**80px**</span></span>|<span data-ttu-id="ec7b3-168">**96px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-168">**96px**</span></span>|
|:---|:---|:---|:---|:---|:---|:---|:---|:---|
|![16ピクセルアイコン](../images/monolineicon7.png)|![20ピクセルアイコン](../images/monolineicon8.png)|![24 px アイコン](../images/monolineicon9.png)|![32 px アイコン](../images/monolineicon10.png)|![40 px アイコン](../images/monolineicon11.png)|![48 px アイコン](../images/monolineicon12.png)|![64 px アイコン](../images/monolineicon13.png)|![80 px アイコン](../images/monolineicon14.png)|![96 px アイコン](../images/monolineicon15.png)|

#### <a name="line-weights"></a><span data-ttu-id="ec7b3-178">線の太さ</span><span class="sxs-lookup"><span data-stu-id="ec7b3-178">Line weights</span></span>

<span data-ttu-id="ec7b3-179">Monoline は、線とアウトライン付きの図形のスタイルです。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-179">Monoline is a style dominated by line and outlined shapes.</span></span> <span data-ttu-id="ec7b3-180">アイコンのサイズに応じて、次の線の太さを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-180">Depending on what size you are producing the icon should use the following line weights.</span></span>

|<span data-ttu-id="ec7b3-181">**アイコンのサイズ:**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-181">**Icon Size:**</span></span>|<span data-ttu-id="ec7b3-182">**16px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-182">**16px**</span></span>|<span data-ttu-id="ec7b3-183">**20px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-183">**20px**</span></span>|<span data-ttu-id="ec7b3-184">**24px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-184">**24px**</span></span>|<span data-ttu-id="ec7b3-185">**32px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-185">**32px**</span></span>|<span data-ttu-id="ec7b3-186">**40px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-186">**40px**</span></span>|<span data-ttu-id="ec7b3-187">**48px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-187">**48px**</span></span>|<span data-ttu-id="ec7b3-188">**64px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-188">**64px**</span></span>|<span data-ttu-id="ec7b3-189">**80px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-189">**80px**</span></span>|<span data-ttu-id="ec7b3-190">**96px**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-190">**96px**</span></span>|
|:---|:---|:---|:---|:---|:---|:---|:---|:---|:---|
|<span data-ttu-id="ec7b3-191">**線の太さ:**</span><span class="sxs-lookup"><span data-stu-id="ec7b3-191">**Line Weight:**</span></span>|<span data-ttu-id="ec7b3-192">1px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-192">1px</span></span>|<span data-ttu-id="ec7b3-193">1px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-193">1px</span></span>|<span data-ttu-id="ec7b3-194">1px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-194">1px</span></span>|<span data-ttu-id="ec7b3-195">1px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-195">1px</span></span>|<span data-ttu-id="ec7b3-196">2px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-196">2px</span></span>|<span data-ttu-id="ec7b3-197">2px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-197">2px</span></span>|<span data-ttu-id="ec7b3-198">2px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-198">2px</span></span>|<span data-ttu-id="ec7b3-199">2px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-199">2px</span></span>|<span data-ttu-id="ec7b3-200">3px</span><span class="sxs-lookup"><span data-stu-id="ec7b3-200">3px</span></span>|
||![16ピクセルアイコン](../images/monolineicon16.png)|![20ピクセルアイコン](../images/monolineicon17.png)|![24 px アイコン](../images/monolineicon18.png)|![32 px アイコン](../images/monolineicon19.png)|![40 px アイコン](../images/monolineicon20.png)|![48 px アイコン](../images/monolineicon21.png)|![64 px アイコン](../images/monolineicon22.png)|![80 px アイコン](../images/monolineicon23.png)|![96 px アイコン](../images/monolineicon24.png)|

#### <a name="cutouts"></a><span data-ttu-id="ec7b3-210">切り抜き</span><span class="sxs-lookup"><span data-stu-id="ec7b3-210">Cutouts</span></span>

<span data-ttu-id="ec7b3-211">Icon 要素が別の要素の上に配置されている場合は、主に読みやすくするために、(bottom 要素の) 切り抜きを使用して、2つの要素の間にスペースを提供します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-211">When an icon element is placed on top of another element, a cutout (of the bottom element) is used to provide space between the two elements, mainly for readability purposes.</span></span> <span data-ttu-id="ec7b3-212">これは通常、修飾子が基本要素の上に配置されている場合に、いずれの要素も修飾子ではない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-212">This usually happens when a modifier is placed on top of a base element, but there are also cases where neither of the elements is a modifier.</span></span> <span data-ttu-id="ec7b3-213">これらの2つの要素間の切り抜きは、「gap」と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-213">These cutouts between the two elements is sometimes referred to as a "gap".</span></span>

<span data-ttu-id="ec7b3-214">間隔のサイズは、そのサイズに対して使用される線の太さと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-214">The size of the gap should be the same width as the line weight used on that size.</span></span> <span data-ttu-id="ec7b3-215">16ピクセルのアイコンを作成する場合は、間隔を1px に設定し、それが48ピクセルのアイコンの場合、ギャップを2px にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-215">If making a 16px icon, the gap width would be 1px and if it is a 48px icon then the gap should be 2px.</span></span> <span data-ttu-id="ec7b3-216">次の例では、修飾子と基になるベースとの間に1px のギャップがある間隔アイコンを示しています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-216">The following example shows a 32px icon with a gap of 1px between the modifier and the underlying base.</span></span>

![修飾子と基になるベースとの間に1px のギャップがある間隔アイコン](../images/monolineicon25.png)

<span data-ttu-id="ec7b3-218">場合によっては、スペースが斜めまたは曲線のエッジを持つ場合は、1/2px で間隔を増やすことができ、標準のギャップでは十分な分離が得られない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-218">In some cases, the gap can be increase by a 1/2px if the modifier has a diagonal or curved edge and the standard gap doesn't provide enough separation.</span></span> <span data-ttu-id="ec7b3-219">これは、1px 線の太さを持つアイコンにのみ影響する可能性があります。16px、20px、24px、および32px。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-219">This will likely only affect the icons with 1px line weight; 16px, 20px, 24px, and 32px.</span></span>

#### <a name="background-fills"></a><span data-ttu-id="ec7b3-220">背景の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="ec7b3-220">Background fills</span></span>

<span data-ttu-id="ec7b3-221">Monoline アイコンセットのほとんどのアイコンは、背景の塗りつぶしを必要とします。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-221">Most icons in the Monoline icon set require background fills.</span></span> <span data-ttu-id="ec7b3-222">ただし、オブジェクトが自然に塗りつぶされていない場合は、塗りつぶしを適用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-222">However, there are cases where the object would not naturally have a fill, so no fill should be applied.</span></span> <span data-ttu-id="ec7b3-223">次のアイコンには白の塗りつぶしが設定されています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-223">The following icons have a white fill:</span></span>

![5つのアイコンに白の塗りつぶしが設定されている](../images/monolineicon26.png)

<span data-ttu-id="ec7b3-225">次のアイコンには塗りつぶしがありません。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-225">The following icons have no fill.</span></span> <span data-ttu-id="ec7b3-226">(中央の穴が塗りつぶされていないことを示す歯車アイコンが含まれています)。![塗りつぶしなしの5つのアイコン](../images/monolineicon27.png)</span><span class="sxs-lookup"><span data-stu-id="ec7b3-226">(The gear icon is included to show that the center hole is not filled.) ![Five icons with no fill](../images/monolineicon27.png)</span></span>

##### <a name="best-practices-for-fills"></a><span data-ttu-id="ec7b3-227">塗りつぶしのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="ec7b3-227">Best practices for fills</span></span>

###### <a name="dos"></a><span data-ttu-id="ec7b3-228">Do</span><span class="sxs-lookup"><span data-stu-id="ec7b3-228">Dos:</span></span>

- <span data-ttu-id="ec7b3-229">境界が定義されている任意の要素を塗りつぶします。塗りつぶしがあります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-229">Fill any element that has a defined boundary, and would naturally have a fill.</span></span>
- <span data-ttu-id="ec7b3-230">背景の塗りつぶしを作成するには、別の図形を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-230">Use a separate shape to create the background fill.</span></span>
- <span data-ttu-id="ec7b3-231">[カラーパレット](#color)から**背景の塗りつぶし**を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-231">Use **Background Fill** from the [color palette](#color).</span></span>
- <span data-ttu-id="ec7b3-232">重なり合う要素間のピクセルの間隔を維持します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-232">Maintain the pixel separation between overlapping elements.</span></span>
- <span data-ttu-id="ec7b3-233">複数のオブジェクト間での塗りつぶし。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-233">Fill between multiple objects.</span></span>

###### <a name="donts"></a><span data-ttu-id="ec7b3-234">注意事項</span><span class="sxs-lookup"><span data-stu-id="ec7b3-234">Don'ts:</span></span>

- <span data-ttu-id="ec7b3-235">自然に入力されていないオブジェクトを塗りつぶすことはできません。たとえば、クリップになります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-235">Don't fill objects that would not naturally be filled; for example, a paperclip.</span></span>
- <span data-ttu-id="ec7b3-236">角かっこを入力しません。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-236">Don't fill brackets.</span></span>
- <span data-ttu-id="ec7b3-237">数字または英字の後ろには入力しないでください。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-237">Don't fill behind numbers or alpha characters.</span></span>

### <a name="color"></a><span data-ttu-id="ec7b3-238">色</span><span class="sxs-lookup"><span data-stu-id="ec7b3-238">Color</span></span>

<span data-ttu-id="ec7b3-239">カラーパレットは、シンプルかつアクセシビリティを目的として設計されています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-239">The color palette has been designed for simplicity and accessibility.</span></span> <span data-ttu-id="ec7b3-240">この中には、4つの中間色の色と、青、緑、黄色、赤、および紫の2つのバリエーションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-240">It contains 4 neutral colors and two variations for blue, green, yellow, red, and purple.</span></span> <span data-ttu-id="ec7b3-241">オレンジ色は、意図的に Monoline アイコンカラーパレットに含まれていません。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-241">Orange is intentionally not included in the Monoline icon color palette.</span></span> <span data-ttu-id="ec7b3-242">各色は、このセクションで説明する特定の方法で使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-242">Each color is intended to be used in specific ways as outlined in this section.</span></span>

#### <a name="palette"></a><span data-ttu-id="ec7b3-243">カラー</span><span class="sxs-lookup"><span data-stu-id="ec7b3-243">Palette</span></span>

![Monoline の4つの灰色の網掛け](../images/monoline-grayshades.png)

![Monoline のカラーパレット](../images/monoline-colors.png)

#### <a name="how-to-use-color"></a><span data-ttu-id="ec7b3-246">色の使用方法</span><span class="sxs-lookup"><span data-stu-id="ec7b3-246">How to use color</span></span>

<span data-ttu-id="ec7b3-247">Monoline カラーパレットでは、すべての色に、スタンドアロン、アウトライン、および塗りつぶしのバリエーションがあります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-247">In the Monoline color palette, all colors have Standalone, Outline, and Fill variations.</span></span> <span data-ttu-id="ec7b3-248">通常、要素は塗りつぶしと輪郭で構成されています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-248">Generally, elements are constructed with a fill and a border.</span></span> <span data-ttu-id="ec7b3-249">色は、次のいずれかのパターンで適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-249">The colors are applied in one of the following patterns:</span></span>

- <span data-ttu-id="ec7b3-250">塗りつぶしが設定されていないオブジェクトのスタンドアロンカラーのみ。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-250">The Standalone color alone for objects that have no fill.</span></span>
- <span data-ttu-id="ec7b3-251">罫線はアウトラインの色を使用し、塗りつぶしには塗りつぶしの色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-251">The border uses the Outline color and the fill uses the Fill color.</span></span>
- <span data-ttu-id="ec7b3-252">罫線は、スタンドアロンの色を使用し、塗りつぶしには背景の塗りつぶしの色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-252">The border uses the Standalone color and the fill uses the Background Fill color.</span></span>

<span data-ttu-id="ec7b3-253">次に色を使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-253">The following are examples of using color.</span></span>

![色が罫線または塗りつぶしの3つのアイコン](../images/monolineicon28.png)

<span data-ttu-id="ec7b3-255">最も一般的な状況は、要素に背景の塗りつぶしを使用して濃い灰色のスタンドアロンを使用することです。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-255">The most common situation will be to have an element use Dark Gray Standalone with Background Fill.</span></span>

<span data-ttu-id="ec7b3-256">色の塗りつぶしを使用する場合は、常に、対応する輪郭の色で表示される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-256">When using a colored Fill, it should always be with its corresponding Outline color.</span></span> <span data-ttu-id="ec7b3-257">たとえば、青い塗りつぶしは青い輪郭線でのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-257">For example, Blue Fill should only be used with Blue Outline.</span></span> <span data-ttu-id="ec7b3-258">ただし、この一般的なルールには次の2つの例外があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-258">But there are two exceptions to this general rule:</span></span>

- <span data-ttu-id="ec7b3-259">背景の塗りつぶしは、任意の色のスタンドアロンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-259">Background Fill can be used with any color Standalone.</span></span>
- <span data-ttu-id="ec7b3-260">明るい灰色の塗りつぶしは、2つの異なる輪郭の色 (濃い灰色または淡い灰色) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-260">Light Gray Fill can be used with two different Outline colors: Dark Gray or Medium Gray.</span></span>

#### <a name="when-to-use-color"></a><span data-ttu-id="ec7b3-261">色を使用する場合</span><span class="sxs-lookup"><span data-stu-id="ec7b3-261">When to use color</span></span>

<span data-ttu-id="ec7b3-262">装飾記号ではなく、アイコンの意味を伝えるために色を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-262">Color should be used to convey the meaning of the icon rather than for embellishment.</span></span> <span data-ttu-id="ec7b3-263">ユーザーに対する**アクションを強調表示**する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-263">It should **highlight the action** to the user.</span></span> <span data-ttu-id="ec7b3-264">色が設定された基本要素に修飾子を追加すると、通常、基本要素は濃い灰色と背景の塗りつぶしに変更されます。この場合、次の例のように、先頭の左端にある picture base に "X" という修飾子を追加します。次のセットの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-264">When a modifier is added to a base element that has color, the base element is typically turned into Dark Gray and Background Fill so that the modifier can be the element of color, such as the case below with the "X" modifier being added to the picture base in the leftmost icon of the following set.</span></span>

![色を使用する5つのアイコン](../images/monolineicon29.png)

<span data-ttu-id="ec7b3-266">アイコンは、前に説明したアウトラインと塗りつぶし以外の**1 つ**の追加色に制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-266">You should limit your icons to **one** additional color, other than the Outline and Fill mentioned above.</span></span> <span data-ttu-id="ec7b3-267">ただし、メタファにとって重要であり、灰色以外の2つの追加の色の制限がある場合は、より多くの色を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-267">However, more colors can be used if it is vital for its metaphor, with a limit of two additional colors other than gray.</span></span> <span data-ttu-id="ec7b3-268">その他の色を必要とする場合、例外が発生することがまれにあります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-268">In rare cases, there are exceptions when more colors are needed.</span></span> <span data-ttu-id="ec7b3-269">次に示すのは、1つの色のみを使用するアイコンの適切な例です。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-269">The following are good examples of icons that use just one color.</span></span>

  ![それぞれ1色の5つのアイコンの画像](../images/monolineicon30.png)

<span data-ttu-id="ec7b3-271">しかし、次のアイコンは多くの色を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-271">But the following icons use too many colors.</span></span>

  ![複数の色がある5つのアイコンの画像](../images/monolineicon31.png)


<span data-ttu-id="ec7b3-273">内部の "コンテンツ" (スプレッドシートのアイコン内のグリッド線など) に**淡い灰色**を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-273">Use **Medium Gray** for interior "content", such as grid lines in an icon of a spreadsheet.</span></span> <span data-ttu-id="ec7b3-274">コンテンツにコントロールの動作を表示する必要がある場合は、追加の内部色が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-274">Additional interior colors are used when the content needs to show the behavior of the control.</span></span>

![灰色の淡い要素を含む5つのアイコン](../images/monolineicon32.png)

#### <a name="text-lines"></a><span data-ttu-id="ec7b3-276">テキスト行</span><span class="sxs-lookup"><span data-stu-id="ec7b3-276">Text lines</span></span>

<span data-ttu-id="ec7b3-277">テキスト行が "container" (たとえば、ドキュメントのテキスト) にある場合は、淡い灰色を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-277">When text lines are in a "container" (for example, text on a document), use medium gray.</span></span> <span data-ttu-id="ec7b3-278">コンテナー内にないテキスト行は、**濃い灰色**にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-278">Text lines not in a container should be **Dark Gray**.</span></span>

### <a name="text"></a><span data-ttu-id="ec7b3-279">テキスト</span><span class="sxs-lookup"><span data-stu-id="ec7b3-279">Text</span></span>

<span data-ttu-id="ec7b3-280">アイコンでテキスト文字を使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-280">Avoid using text characters in icons.</span></span> <span data-ttu-id="ec7b3-281">Office 製品は世界中で使用されているため、アイコンをできるだけニュートラルにしておきたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-281">Since Office products are used around the world, we want to keep icons as language neutral as possible.</span></span>

## <a name="production"></a><span data-ttu-id="ec7b3-282">運用</span><span class="sxs-lookup"><span data-stu-id="ec7b3-282">Production</span></span>

### <a name="icon-file-format"></a><span data-ttu-id="ec7b3-283">アイコンファイルの形式</span><span class="sxs-lookup"><span data-stu-id="ec7b3-283">Icon file format</span></span>

<span data-ttu-id="ec7b3-284">最終的なアイコンは .png 画像ファイルとして保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-284">The final icons should be saved as .png image files.</span></span> <span data-ttu-id="ec7b3-285">透明な背景で PNG 形式を使用し、32ビットの深さを設定します。</span><span class="sxs-lookup"><span data-stu-id="ec7b3-285">Use PNG format with a transparent background and have 32-bit depth.</span></span>