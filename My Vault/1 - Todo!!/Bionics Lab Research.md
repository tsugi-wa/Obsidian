---
Urgency: "!!!"
Date Due: 9/6/2024 4:35 AM
---
2ttps://drive.google.com/file/d/1CBr2VrJ_E4DDDXAQUsh_ADIHlsySbTGx/view?usp=drive_link

- [x] call caleb with returnsumdata true
- [x] rename "grace" "caleb" in 1x3 graphs
- [ ] fix 6x3 graph ignore index01x, index02x, index02y and plot thumb
- [x] final trim version in 1x3 plot
- [ ] adapt to new seungmin folder system, ignore w/out hand sensor
- [ ] output sum of degrees and normalized degrees to csv
- [x] calculate avg and sum for normalization
- [x] 201 to 200 
- [ ] range of motion
- [ ] save sum of data into csv


# Helpers:
```
def get_testno(filename):
	return 0 for test 1, etc.
	*testnames, testnames_alt*

def interpolate_to_0_2(df):
	given df, return interpolated df

def get_hand(filename):
	return hand[0] if left in filename, etc.
	*hands*

def generate_colors(num_colors, plot_colors=False):
	generate x many numbers, choose to preview colors

def mean_smooth(y, window_size=15):
	compute mean_smooth with same len as before

def smooth_data(df, col_name, threshold):
	In-place, removal of sensor jumps

def compute_ratio(df, base, joint1, joint2, output_col_name, smooth_output=True):
	first smoothes all 3 given cols then compute dist and ratio
	ratio's name is output_col_name
	dist naming convention:
	base + "—" + joint1 + "_dist"
	does IN-PLACE

def no_scroll():
	disables scrolling window	
```
# Grapher
```
def graph_files(files, files_untrimmed, testno, hand, output_name,       
  deg_min_max, ratio_min_max, dist_min_max,
	9x4 graph

def graph_all_scores(score2_files, score1_files, score0_files, 
  score2_files_untrimmed, score1_files_untrimmed, score0_files_untrimmed,
  hand, output_name, deg_min_max, save_path=None, hide_plot=False):
	
```