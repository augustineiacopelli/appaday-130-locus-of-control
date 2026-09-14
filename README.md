# AppADay 130: Locus of Control

A single-page reflection tool that takes whatever situation you are carrying and sorts it into three buckets: what is fully in your control, what you might influence but do not decide, and what is not in your control at all.

## What it does

You type the situation the way you would say it out loud. Claude reads it and returns three lists plus a set of weights, and the app renders that as a bullseye. The innermost ring is what you control, the middle ring is what you might influence, and the outer ring is everything else. The rings are sized by area rather than radius so the visual proportions are honest, and each ring is drawn from a cumulative square root of its weight.

The weights matter more than the item counts, and the model is told so explicitly. A single crushing fact you cannot control is allowed to outweigh six small chores you can. A display floor keeps any bucket from collapsing to an invisible sliver on screen, but that floor never touches the real numbers shown in the legend and the history. The weights are forced to three integers summing to exactly 100 by largest remainder, with a fallback to item count proportions if the model returns nothing usable.

Every item carries a step, and the kind of step depends on the bucket it landed in. Controllable items get a small concrete first move you could start today. Influenceable items get one attempt at influence worded so the outcome stays open. Uncontrollable items get a practice of acceptance, release, or attention shifting rather than an action item that pretends the thing is yours to fix. The system prompt forbids diagnostic language outright, and it forbids dismissing or minimizing feelings about the uncontrollable bucket.

Items can be checked off as done, and that state saves immediately. History keeps every entry, newest first, and adds two things on top of the list. A trend line tracks the share of each situation that was actually in your control across entries, drawn as a small inline sparkline. A recurring worry report flags any uncontrollable item that has now shown up in three or more separate entries, which is usually the most useful thing on the page.

## Build

Single `index.html` file. Inline CSS and vanilla JavaScript, no frameworks, no build step. Google Fonts (Fraunces, Inter) via CDN is the only external dependency besides the Claude API call. The bullseye is inline SVG rather than canvas. Your Anthropic API key lives in the Settings modal and is stored in your browser's local storage only, never committed and never sent anywhere except directly to Anthropic.

## Category

AppADay category H, Health and Wellness, with `ai:true`. The Claude call is the core function rather than an enhancement layer, so the app does nothing until a key is saved.

## Not therapy

This is a self reflection tool. It does not diagnose anything and it is no substitute for talking with a professional or someone who knows you.
