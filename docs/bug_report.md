# Lemon Clicker Bug Report

**Name:** Kevin Chau
**Tickets solved:** <!-- e.g. 1, 2, 3, 5, 6 (at least five) -->

Copy the template below once for each ticket you solved. 

---


## Ticket <1>: <ticket Stats always say "Stats unavailable">

### Actual cause

**File / function:** `src/screens/MenuScreen/MenuScreenController.ts` / `loadStatsFromServer()`

**What was wrong:** In the menu screen controller there was an issue with the function `loadStatsFromServer()` because it had the incorrect API route.

### Fix

I replaced the spelling in `loadStatsFromServer()`.

### How did you find it?

I found it by seeing which function threw the error message that I saw in the menu screen, which was the function `loadStatsFromServer()`. If the response is none from the API route, then it would throw the error "Unable to load stats".

#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**

I initially was searching for the function that threw the error "Unable to load stats" and I saw that it only throws that error if the API route didn't respond with anything, so I traced it back to `loadStatsFromServer()`.

#### Backward tracing

1. **Symptom:** I saw an error thrown on the menu page saying that the leaderboard couldn't be shown.
2. **Traced back to:** `loadStatsFromServer()`
3. **Traced back to:** `app.get("/api/stats", (_req, res)`
4. **Buggy code:** Line 45 of `index.ts` is spelled `/stats` and not `stat`, so I replaced the spelling in the function `loadStatsFromServer()`.

### Confirming the fix

After I replaced the spelling, it started showing the most recent score.

## Ticket <2>: <ticket title>

### Actual cause

**File / function:** `src/screens/MenuScreen/MenuScreenController.ts` / `loadStatsFromServer()`

**What was wrong:** In the menu screen controller there was an issue with the function `loadStatsFromServer()` because it had the incorrect API route.

### Fix

I replaced the spelling in `loadStatsFromServer()`.

### How did you find it?

I found it by seeing which function threw the error message that I saw in the menu screen, which was the function `loadStatsFromServer()`. If the response is none from the API route, then it would throw the error "Unable to load stats".

#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**

I initially was searching for the function that threw the error "Unable to load stats" and I saw that it only throws that error if the API route didn't respond with anything, so I traced it back to `loadStatsFromServer()`.

#### Backward tracing

1. **Symptom:** I saw an error thrown on the menu page saying that the leaderboard couldn't be shown.
2. **Traced back to:** `loadStatsFromServer()`
3. **Traced back to:** `app.get("/api/stats", (_req, res)`
4. **Buggy code:** Line 45 of `index.ts` is spelled `/stats` and not `stat`, so I replaced the spelling in the function `loadStatsFromServer()`.

### Confirming the fix

After I replaced the spelling, it started showing the most recent score.

## Ticket <2>: <ticket Stats always say "Stats unavailable">

### Actual cause

**File / function:** `/server/index.ts` / `app.get("/api/stats", (_req, res)`

**What was wrong:** In the menu screen controller there was an issue with the function `app.get("/api/stats", (_req, res)` because it had the incorrect API route.

### Fix

I replaced the spelling in `app.get("/api/stats", (_req, res)`.

### How did you find it?

I found it by seeing which function was responsible for the logic of the showing of the best scores which was  `app.get("/api/stats", (_req, res)` it looped throguh
#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**
 `app.get("/api/stats", (_req, res)`

#### Backward tracing

1. **Symptom:** I saw an error thrown on the menu page saying that the leaderboard couldn't be shown.
2. **Traced back to:** `app.get("/api/stats", (_req, res)`
3. **Traced back to:** `app.get("/api/stats", (_req, res)`
4. **Buggy code:** Line 45 of `index.ts` is spelled `/stats` and not `stat`, so I replaced the spelling in the function `app.get("/api/stats", (_req, res)`.

### Confirming the fix

After I replaced the spelling, it started showing the most recent score.

## Ticket <2>: <ticket Best score always shows 0>

### Actual cause

**File / function:** `server/index.ts` / `app.get("/api/stats", (_req, res)`

**What was wrong:** In the server/index.ts there was a loop that set the best score to any entry that is <= the best score at the time which was always 0 so it wouldn't overwrite the best score with a higher score.

### Fix

I replaced the <= operator with the >= operator in order to seee which entries are greater than my best score and if its greater then I replace the score
### How did you find it?

I found it by seeing which function  was responsible for setting the best score 

#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**

I was searching for the best score and I knew that the route for getting the stats was in the index.ts so I checked there and I found the api route that replaced best score with teh highest score from each entry and I saw that it was replacing when the entry was less than the best score instead of greater than .

#### Backward tracing

### Confirming the fix

After I replaced the spelling, it started showing the greatest score.

## Ticket 3: Lemon only jumps to the corners

### Actual cause

**File / function:** `src/screens/GameScreen/GameScreenView.ts` / `randomizeLemonPosition()`

**What was wrong:** `Math.round` was wrapped around only `Math.random()`. `Math.random()` returns a decimal from 0 up to 1, and rounding that decimal gives only 0 or 1. That 0 or 1 was then multiplied by the allowed range. So `randomX` was only ever `minX` or `maxX`, and `randomY` was only ever `minY` or `maxY`. The lemon could only appear at the four corners of the padded area.

### Fix

I moved the parentheses so `Math.round` wraps the whole position, not just `Math.random()`:

`Math.round(Math.random() * (maxX - minX) + minX)`

`Math.random()` is scaled across the range from `minX` to `maxX` first, and then that result is rounded to a pixel. The same change was made for `randomY`.

### How did you find it?

Clicking the lemon was supposed to move it to a random spot, but it only showed up at the corners. I looked at `randomizeLemonPosition()`, which is what runs after a click, and checked how `randomX` and `randomY` were calculated.

#### Hypothesis testing

**What hypothesis ultimately led you to identify the buggy code, and why?**

I thought the random formula was collapsing to the edges. `Math.round(Math.random())` is 0 about half the time and 1 the other half, so multiplying that by `(maxX - minX)` only produces the left limit or the right limit. That matches a lemon that only jumps to the corners.

#### Backward tracing

1. **Symptom:** After a click, the lemon only appeared at the corners.
2. **Traced back to:** `handleLemonClick()` in `GameScreenController.ts`, which calls `this.view.randomizeLemonPosition()`.
3. **Traced back to:** `randomizeLemonPosition()` in `GameScreenView.ts`, where `randomX` and `randomY` are set from `minX`, `maxX`, `minY`, and `maxY`.
4. **Buggy code:** The original lines were `Math.round(Math.random()) * (maxX - minX) + minX` and the same pattern for `randomY`. The rounding function was applied before we multipled the random value to the 

### Confirming the fix

After moving `Math.round` to cover the outside of this expression `Math.random()) * (maxX - minX) + minX` then it starting appearing out of the corners.

