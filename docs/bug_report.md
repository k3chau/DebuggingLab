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

