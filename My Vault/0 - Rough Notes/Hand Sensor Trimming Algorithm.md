## Documentation for How to Trim: 
1. smooth jumps
2. compute dist and dist ratios and smooth that
3. set timestamp min-max to 0-2
4. pick degree column with greatest range and calculate additional col of mean-smoothed version (window size=10)
5. interpolate dataframe (200 steps) 
6. get normalize untrimmed unflipped interpolated (200 steps) dataframe
7. clip data:
	based on mean-smoothed max range degree col's gradient
	threshold is 15% of absolute max gradient
	iterate left to right until threshold hit:
		if hit, then check if cutting at that part results in new smoothed degree col's range < 95% of original smoothed degree col's range. If so, then revert to 0 or previous hit
		otherwise save hit and try again

		if thumb, then cut out the thumb open from calibrate position
	same with end idx cut, but iterate right to left.