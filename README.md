# KIET_AI_DebugChallenge

# Bugs
Bug 2 → Crash immediately: vocabulary is empty since all text tokens are letters, never digits

Bug 3 + 4 → Training runs but loss never decreases; accuracy stays near random (model gets zero-vector inputs and wrong gradients)

Bug 5 → Training looks successful, but during chat the bot always says "I don't understand" because threshold 0.95 is almost never reached

Bug 1 → Even after fixing bugs 2–5, the bot still refuses every response — students must find the config value 

The bugs are ordered by discovery difficulty, forcing students to debug in layers: crash → training failure → inference failure.

Fixes:
=> Changed the confidence threshold from 0.95 to 0.70 in chatbot.py (Line -29)
=> Changed to isalpha from isdigit in chatbot.py (Line -42)
=> Changed vec[idx] = 1.0 from 0.0 in chatbot.py (Line -66)
=> Removed the single inverted commas in chatbot.py (Line -116)
=> dtanh  = (1.0 - self._hs[t + 1] ** 2) * d_h   # tanh derivative #changed + to - in chatbot.py (Line -118)


