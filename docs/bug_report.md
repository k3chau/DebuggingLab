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

After I replaced the spelling, it started showing the greatest score

